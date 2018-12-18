---
title: Creazione di istanze di Editor di componenti di base tramite l'API Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a720126324faf1ab9a9a4e07086bc4ec711508f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Creazione di istanze di Editor di componenti di base tramite l'API Legacy
L'editor è responsabile per la modifica delle funzioni, ad esempio inserimento, eliminazione, copia e Incolla di testo. Combina queste funzioni con quelli forniti da servizi di linguaggio, ad esempio la colorazione di testo, i rientri e il completamento delle istruzioni IntelliSense.  
  
 È possibile creare un'istanza dell'editor di componenti di base in uno dei tre modi:  
  
-   Creare in modo esplicito un'istanza del core editor in una finestra.  
  
-   Fornire un factory dell'editor che restituisce un'istanza dell'editor di componenti di base  
  
-   Aprire un file dalla gerarchia di progetto.  
  
 Nelle sezioni seguenti viene illustrato come utilizzare l'API legacy per creare un'istanza di editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Apertura in modo esplicito un'istanza dell'Editor di componenti di base  
 Durante il recupero in modo esplicito un'istanza dell'editor di componenti di base:  
  
-   Ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per contenere l'oggetto dati del documento in fase di modifica.  
  
-   Creare una rappresentazione riga orientata ai servizi dell'oggetto dati del documento tramite la creazione di un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaccia dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaccia.  
  
-   Impostare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> come l'oggetto dati del documento per un'istanza dell'implementazione predefinita del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfaccia, utilizzando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> metodo.  
  
     Host di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> dell'istanza in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> metodo.  
  
 A questo punto, la visualizzazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia fornisce una finestra che contiene un'istanza dell'editor di componenti di base.  
  
 Tuttavia, ciò non è un'istanza molto utile, perché non dispone di tasti di scelta rapida o accedere alle funzionalità avanzate. Per ottenere l'accesso alle funzionalità avanzate e tasti di scelta rapida:  
  
-   Utilizzare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo per associare un servizio di linguaggio e l'oggetto dati del documento che utilizza l'editor.  
  
-   Creare la propria tasti di scelta rapida oppure utilizzare l'impostazione predefinita impostando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetti visualizzare le proprietà. A tale scopo, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metodo con il <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> proprietà.  
  
     Per ottenere e utilizzare i tasti di scelta rapida non standard, generarli utilizzando il file con estensione vsct. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Come utilizzare una factory dell'Editor per ottenere l'Editor di componenti di base  
 Quando si implementa un editor di componenti di base con un factory di editor utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo), eseguire tutti i passaggi descritti nella sezione precedente per ospitare in modo esplicito un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> utilizzando un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> dell'oggetto dati del documento, in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto.  
  
 Per visualizzare il testo, ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> oggetto e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo.  
  
 Per fornire un servizio di linguaggio per l'editor, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo all'interno di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo.  
  
 Per ottenere predefinito tasti di scelta rapida, a differenza della sezione precedente, utilizzare il contesto del comando restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo quando l'editor di componenti di base da ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo.  
  
 Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo restituisce il comando stesso GUID come editor di testo, l'istanza dell'editor di componenti di base ottiene automaticamente il valore predefinito tasti di scelta rapida.  
  
 Per informazioni generali, vedere [procedura dettagliata: creazione di un Editor di componenti di base e la registrazione di un tipo di File Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)