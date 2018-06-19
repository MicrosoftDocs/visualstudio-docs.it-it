---
title: Creazione di una finestra degli strumenti di multi-istanza | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 910ca8f223d5f4f37242990ba7384afb0dbebd7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097796"
---
# <a name="creating-a-multi-instance-tool-window"></a>Creazione di una finestra degli strumenti di multi-istanza
È possibile programmare una finestra degli strumenti in modo che più istanze possono essere aperte contemporaneamente. Per impostazione predefinita, le finestre degli strumenti possono essere solo un'istanza aperto.  
  
 Quando si utilizza una finestra degli strumenti di multi-istanza, è possibile mostrare diverse correlate fonti di informazioni allo stesso tempo. Ad esempio, è possibile inserire una multi-riga <xref:System.Windows.Forms.TextBox> controllare in una finestra degli strumenti di multi-istanza in modo che siano disponibili contemporaneamente diversi frammenti di codice durante una sessione di programmazione. Inoltre, ad esempio, è possibile inserire un <xref:System.Windows.Forms.DataGrid> casella controllo e un elenco a discesa in una finestra degli strumenti a più istanze in modo che sia possibile rilevare numerose origini dati in tempo reale contemporaneamente.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Creazione di una finestra degli strumenti di base (a istanza singola)  
  
1.  Creare un progetto denominato **MultiInstanceToolWindow** utilizzando il modello di progetto VSIX e aggiungere un modello di elemento della finestra dello strumento personalizzato denominato **MIToolWindow**.  
  
    > [!NOTE]
    >  Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Esecuzione di multi-un'istanza di strumento  
  
1.  Aprire il **MIToolWindowPackage.cs** file e individuare il `ProvideToolWindow` attributo. e il `MultiInstances=true` parametro, come illustrato nell'esempio seguente:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  Nel file MIToolWindowCommand.cs, trovare il metodo ShowToolWindos(). In questo metodo, chiamare il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo e impostare il relativo `create` flag `false` in modo che scorrerà istanze esistenti di finestra strumento finché non è disponibile un `id` viene trovato.  
  
3.  Per creare un'istanza dello strumento, chiamare il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo e impostare il relativo `id` su un valore disponibile e il relativo `create` flag `true`.  
  
     Per impostazione predefinita, il valore della `id` parametro del <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo `0`. Questo valore consente di una finestra degli strumenti a istanza singola. Per più di un'istanza deve essere ospitato, ogni istanza deve avere un proprio univoco `id`.  
  
4.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto restituito dal <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> proprietà dell'istanza di finestra dello strumento.  
  
5.  Per impostazione predefinita, il `ShowToolWindow` metodo che viene creato dal modello di elemento di finestra dello strumento consente di creare una finestra degli strumenti a istanza singola. Nell'esempio seguente viene illustrato come modificare il `ShowToolWindow` metodo per creare più istanze.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```