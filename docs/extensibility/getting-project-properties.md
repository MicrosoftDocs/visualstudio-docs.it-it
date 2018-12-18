---
title: "Recupero delle proprietà progetto | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 58a24a37de7986ef47acb916d488bd4661c5a4d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-project-properties"></a>Recupero delle proprietà di progetto
Questa procedura dettagliata illustra come proprietà del progetto consente di visualizzare in una finestra degli strumenti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Per creare un progetto VSIX e aggiungere una finestra degli strumenti  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `ProjectPropertiesExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Aggiungere una finestra degli strumenti tramite l'aggiunta di un modello di elemento della finestra degli strumenti personalizzata denominato `ProjectPropertiesToolWindow`. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **finestra di dialogo Aggiungi nuovo elemento**, passare a **elementi di Visual c# / Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel **nome** campo nella parte inferiore della finestra di dialogo, modificare il nome di file in `ProjectPropertiesToolWindow.cs`. Per ulteriori informazioni su come creare una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Compilare la soluzione e verificare che l'operazione avvenga senza errori.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Per visualizzare le proprietà del progetto in una finestra degli strumenti  
  
1.  Nel file ProjectPropertiesToolWindowCommand.cs aggiungere le seguenti istruzioni using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  In ProjectPropertiesToolWindowControl.xaml, rimuovere il pulsante esistente e aggiungere un controllo TreeView dalla casella degli strumenti. È anche possibile rimuovere il gestore dell'evento click dal file ProjectPropertiesToolWindowControl.xaml.cs.  
  
3.  In ProjectPropertiesToolWindowCommand.cs, utilizzare il metodo ShowToolWindow() per aprire il progetto e leggere le relative proprietà, quindi aggiungere le proprietà al controllo TreeView. Il codice per ShowToolWindow dovrebbe essere simile al seguente:  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.  
  
5.  Nell'istanza sperimentale aprire un progetto.  
  
6.  Nel **vista o altre finestre** fare clic su **ProjectPropertiesToolWindow**.  
  
     Verrà visualizzato il controllo struttura ad albero nella finestra degli strumenti con il nome del primo progetto e di tutte le proprietà di progetto.