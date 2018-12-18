---
title: Estendere la finestra di Output | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b9a8b260c1a3cab126d19f0cedc0c1e5362cf81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-output-window"></a>Estendere la finestra di Output
Il **Output** finestra è un set di riquadri di testo di lettura/scrittura. Visual Studio include questi riquadri predefiniti: **compilare**, nella quale i progetti comunicare i messaggi relativi alle compilazioni, e **generale**, in cui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comunica i messaggi relativi a IDE. Progetti di ottengono un riferimento al **compilare** riquadro automaticamente tramita il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metodi di interfaccia e Visual Studio offre accesso diretto al **generale** riquadro tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servizio. Oltre ai riquadri predefiniti, è possibile creare e gestire il propria riquadri personalizzati.  
  
 È possibile controllare il **Output** finestra direttamente tramita il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia, che viene offerto il <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service e definisce i metodi per la creazione, recupero e l'eliminazione definitiva **Output** riquadri della finestra. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia definisce i metodi per la visualizzazione di riquadri, nascondere riquadri e la modifica del testo. Un modo alternativo per il controllo di **Output** finestra viene eseguita tramite il <xref:EnvDTE.OutputWindow> e <xref:EnvDTE.OutputWindowPane> oggetti nel modello a oggetti di automazione di Visual Studio. Questi oggetti includono quasi tutte le funzionalità del <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce. Inoltre, il <xref:EnvDTE.OutputWindow> e <xref:EnvDTE.OutputWindowPane> oggetti aggiungono alcune funzionalità di livello superiore per rendere più semplice enumerare i **Output** riquadri della finestra e per recuperare il testo dai riquadri.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Creazione di un'estensione che utilizza il riquadro di Output  
 È possibile creare un'estensione che utilizza diversi aspetti del riquadro di Output.  
  
1.  Creare un progetto VSIX denominato `TestOutput` con un comando di menu denominato **TestOutput**. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Aggiungere i riferimenti seguenti:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  In TestOutput.cs, aggiungere la seguente istruzione using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  In TestOutput.cs, eliminare il metodo ShowMessageBox. Aggiungere lo stub di metodo seguenti:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  Nel costruttore TestOutput, modificare il gestore del comando per OutputCommandHandler. Di seguito è la parte che aggiunge il comando:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  Nelle sezioni seguenti sono diversi metodi che mostrano i diversi modi per gestire con il riquadro di Output. È possibile chiamare questi metodi al corpo del metodo OutputCommandHandler(). Ad esempio, il codice seguente aggiunge il metodo CreatePane() descritto nella sezione successiva.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Creazione di una finestra di Output con IVsOutputWindow  
 In questo esempio viene illustrato come creare un nuovo **Output** riquadro della finestra utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando verrà visualizzato il **Output** finestra con un'intestazione che indica che **Mostra output da: CreatedPane** e le parole **questo è il riquadro creato** nel riquadro stesso.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Creazione di una finestra di Output con OutputWindow  
 In questo esempio viene illustrato come creare un **Output** riquadro della finestra utilizzando il <xref:EnvDTE.OutputWindow> oggetto.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Sebbene il <xref:EnvDTE.OutputWindowPanes> raccolta consente di recuperare un **Output** riquadro mediante il titolo, i titoli di riquadro non sono necessariamente essere univoco. Quando si dubbi l'univocità di un titolo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metodo per recuperare il riquadro corretto con il relativo GUID.  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando si dovrebbe visualizzare la finestra di Output con un'intestazione che indica che **Mostra output di: DTEPane** e le parole **aggiunto riquadro DTE** nel riquadro stesso.  
  
## <a name="deleting-an-output-window"></a>L'eliminazione di una finestra di Output  
 In questo esempio viene illustrato come eliminare un **Output** riquadro della finestra.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando si dovrebbe visualizzare la finestra di Output con un'intestazione che indica che **Mostra output di: nuovo riquadro** e le parole **aggiunto riquadro creato** nel riquadro stesso. Se si sceglie il **TestOutput richiamare** nuovo il comando, il riquadro viene eliminato.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Recupero di riquadro Generale della finestra di Output  
 In questo esempio viene illustrato come ottenere l'oggetto incorporato **generale** riquadro della finestra di **Output** finestra.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando si noterà che il **Output** finestra vengono visualizzate le parole **trovato generale riquadro** nel riquadro.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Recupero di riquadro compilazione della finestra di Output  
 In questo esempio viene illustrato come trovare il riquadro di compilazione e in scrittura. Poiché il riquadro di compilazione non è attivato per impostazione predefinita, attiva anche.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```