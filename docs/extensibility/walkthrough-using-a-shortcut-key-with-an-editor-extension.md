---
title: "Procedura dettagliata: Utilizzo di un tasto di scelta rapida con un'estensione di Editor | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3d0a9f8f730808cd8179599669342b530f921a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Procedura dettagliata: Utilizzo di un tasto di scelta rapida con un'estensione di Editor
È possibile rispondere a tasti di scelta rapida nell'estensione di editor. La procedura dettagliata seguente viene illustrato come aggiungere un'area di controllo di visualizzazione per una visualizzazione di testo con un tasto di scelta rapida. Questa procedura dettagliata è basata sul modello riquadro di visualizzazione dell'area di controllo editor e consente di aggiungere l'area di controllo utilizzando il carattere +.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo Seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `KeyBindingTest`.  
  
2.  Aggiungere un modello di elemento dell'area di controllo di Editor testo al progetto e denominarlo `KeyBindingTest`. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Aggiungere i seguenti riferimenti e impostare **CopyLocal** a `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Interop  
  
     14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 Nel file di classe KeyBindingTest, modificare il nome della classe per PurpleCornerBox. Utilizzare la lampadina visualizzata nel margine sinistro per apportare le altre modifiche. All'interno del costruttore, modificare il nome del livello di area di controllo dal **KeyBindingTest** a **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>La definizione del filtro di comando  
 Il filtro dei comandi è un'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, che gestisce il comando creando un'area di controllo.  
  
1.  Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandFilter`.  
  
2.  Aggiungere le istruzioni using seguenti.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  La classe denominata KeyBindingCommandFilter deve ereditare da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Aggiungere campi privati per la visualizzazione del testo, il comando successivo nella catena di comando e un flag per rappresentare se è già stato aggiunto il filtro dei comandi.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Aggiungere un costruttore che imposta la visualizzazione del testo.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementare il `QueryStatus()` metodo come indicato di seguito.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementare il `Exec()` metodo in modo che si aggiunge una casella di colore viola alla visualizzazione se un + carattere viene digitato.  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter"></a>Aggiunta del filtro di comando  
 Il provider dell'area di controllo è necessario aggiungere un filtro per la visualizzazione del testo. In questo esempio, il provider implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per ascoltare eventi di creazione visualizzazione di testo. Questo provider dell'area di controllo, inoltre, Esporta il livello di area di controllo, che definisce l'ordine Z dell'area di controllo.  
  
1.  Nel file KeyBindingTestTextViewCreationListener, aggiungere le seguenti istruzioni using:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  Nella definizione del livello dell'area di controllo, modificare il nome del AdornmentLayer da **KeyBindingTest** a **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Per ottenere l'adattatore di visualizzazione di testo, è necessario importare il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Modifica il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che si aggiunge il `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  Il `AddCommandFilter` gestore ottiene l'adattatore di visualizzazione di testo e aggiunge il filtro dei comandi.  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## <a name="making-the-adornment-appear-on-every-line"></a>Effettua l'area di controllo vengono visualizzati su ogni riga  
 L'area di controllo originale era presente in ogni carattere 'a' in un file di testo. Ora che è stato modificato il codice per aggiungere l'area di controllo in risposta al carattere '+', viene aggiunto all'area di controllo solo per la riga in cui il "+" è tipizzata. È possibile modificare il codice dell'area di controllo in modo che l'area di controllo ancora una volta visualizzato su ogni 'a'.  
  
 Nel file KeyBindingTest.cs, modificare il metodo CreateVisuals() per scorrere tutte le righe nella visualizzazione per decorare il carattere 'a'.  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
  
1.  Compilare la soluzione KeyBindingTest ed eseguirlo nell'istanza sperimentale.  
  
2.  Creare o aprire un file di testo. Digitare alcune parole contenenti il carattere 'a', quindi digitare + in qualsiasi punto della visualizzazione di testo.  
  
     Un quadrato di colore viola dovrebbe essere visualizzato ogni carattere 'a' nel file.