---
title: 'Domande frequenti: Conversione di componenti aggiuntivi per le estensioni VSPackage | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 43376b304637ffe59d443ee82350d5492133db2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Domande frequenti: conversione di componenti aggiuntivi in VSPackage Extensions
I componenti aggiuntivi sono deprecati. Per creare una nuova estensione di Visual Studio, è necessario creare un'estensione VSIX. Ecco le risposte ad alcune domande frequenti su come convertire un componente aggiuntivo di Visual Studio in un'estensione VSIX.  
  
> [!WARNING]
>  A partire da Visual Studio 2015, per i progetti c# e Visual Basic, è possibile utilizzare il progetto VSIX e aggiungere i modelli di elementi per i comandi di menu, finestre degli strumenti e VSPackage. Per ulteriori informazioni, vedere [novità di Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  In molti casi è semplicemente possibile trasferire il codice del componente aggiuntivo a un progetto VSIX con un elemento di progetto VSPackage. È possibile ottenere l'oggetto di automazione DTE chiamando <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> nel metodo <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Per ulteriori informazioni, vedere [come è possibile eseguire il codice del componente aggiuntivo in un pacchetto VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) sotto.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Il software necessario per lo sviluppo di estensioni VSIX  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Dove si trova la documentazione di estensione?  
 Iniziare con [iniziando a sviluppare estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Altri articoli sullo sviluppo di estensioni VSSDK in MSDN sono sotto tale.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>È possibile convertire il progetto di componente aggiuntivo a un progetto VSIX?  
 Un progetto di componente aggiuntivo non può essere convertito direttamente a un progetto VSIX perché i meccanismi utilizzati nei progetti VSIX non sono uguali a quelli nei progetti di componente aggiuntivo. Il modello di progetto VSIX, nonché i modelli di progetto di destra hanno una grande quantità di codice che rende relativamente semplice per la configurazione e in esecuzione come un'estensione VSIX.  
  
##  <a name="BKMK_StartDeveloping"></a>Come avviare lo sviluppo di estensioni VSIX?  
 Di seguito viene illustrato come visualizzare un progetto VSIX che dispone di un comando di menu:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Per creare un'estensione VSIX che dispone di un comando di menu  
  
1.  Creare un progetto VSIX. (**File**, **New**, **progetto**, o tipo **progetto** nel **veloce** finestra). Nel **nuovo progetto** finestra di dialogo espandere **Visual c# / Extensibility** o **Visual Basic / Extensibility** e selezionare **progetto VSIX**.) Denominare il progetto **TestExtension** e specificare un percorso relativo.  
  
2.  Aggiungere un **comando personalizzato** il modello di elemento di progetto. (Fare doppio clic sul nodo del progetto nel **Esplora** e selezionare **Aggiungi / nuovo elemento**. Nel **nuovo progetto** finestra di dialogo per Visual c# o Visual Basic, selezionare il **estendibilità** nodo e selezionare **comando personalizzato**.)  
  
3.  Premere F5 per compilare ed eseguire il progetto in modalità di debug.  
  
     Verrà visualizzata una seconda istanza di Visual Studio. Questa seconda istanza è chiamata istanza sperimentale e potrebbe non presentare le stesse impostazioni dell'istanza di Visual Studio che si sta usando per scrivere il codice. La prima volta che si esegue l'istanza sperimentale, verrà richiesto di accedere a Visual Studio Online e specificare il tema e il profilo.  
  
     Nel **strumenti** menu (nell'istanza sperimentale) verrà visualizzato un pulsante denominato **nome comando My**. Quando si sceglie questo pulsante, un messaggio compariranno: **all'interno di TestVSPackagePackage.MenuItemCallback()**.  
  
##  <a name="BKMK_RunAddin"></a>Come è possibile eseguire il codice del componente aggiuntivo in un pacchetto VSPackage?  
 Il codice del componente aggiuntivo viene in genere eseguito in uno dei due modi seguenti:  
  
-   È attivato automaticamente da un comando di menu (il codice si trova nel metodo `IDTCommandTarget.Exec`)  
  
-   Automaticamente all'avvio (il codice si trova nel gestore eventi `OnConnection`)  
  
 È possibile procedere nello stesso modo in un VSPackage. Ecco come è possibile aggiungere il codice del componente aggiuntivo nel metodo di callback:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Per implementare un comando di menu in un VSPackage  
  
1.  Creare un VSPackage contenente un comando di menu. (Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2.  Aprire il file che contiene la definizione del VSPackage. (In un progetto c#, ha  *\<nome progetto >*Package.cs.)  
  
3.  Aggiungere al file le istruzioni `using` seguenti:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Trovare il metodo `MenuItemCallback`. Aggiungere una chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> per recuperare l'oggetto <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Aggiungere il codice presente nel metodo `IDTCommandTarget.Exec` del componente aggiuntivo. Ad esempio, ecco alcuni codice che aggiunge un nuovo riquadro per il **Output** finestra e stampa "Alcune Text" nel nuovo riquadro.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Compilare ed eseguire il progetto. Premere F5 o scegliere **avviare** sul **Debug** barra degli strumenti. Nell'istanza sperimentale di Visual Studio, il **strumenti** menu deve essere un pulsante denominato **nome comando My**. Quando si sceglie questo pulsante, le parole **testo alcune** dovrebbero essere visualizzati in un **Output** riquadro della finestra. (Potrebbe essere necessario aprire il **Output** finestra.)  
  
 È anche possibile scegliere di eseguire il codice all'avvio. Tuttavia, questo approccio è generalmente sconsigliato per le estensioni VSPackage. Se all'avvio di Visual Studio vengono avviate troppe estensioni, il tempo di avvio potrebbe risultare molto più lungo. È invece consigliabile caricare automaticamente l'estensione VSPackage solo in determinate soluzioni, ad esempio all'apertura di una soluzione.  
  
 Questa procedura spiega come aggiungere il codice del componente aggiuntivo in un VSPackage che viene caricato automaticamente all'apertura di una soluzione.  
  
#### <a name="to-autoload-a-vspackage"></a>Per caricare automaticamente un VSPackage  
  
1.  Creare un progetto VSIX con un elemento di progetto di pacchetto di Visual Studio. (Per i passaggi eseguire questa operazione, vedere [come avviare lo sviluppo di estensioni VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). È sufficiente aggiungere il **pacchetto di Visual Studio** dell'elemento di progetto invece.) Denominare il progetto VSIX **TestAutoload**.  
  
2.  Aprire TestAutoloadPackage.cs. Individuare la riga in cui è dichiarata la classe del pacchetto:  
  
    ```csharp  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Sopra questa riga è presente un set di attributi. Aggiungere questo attributo:  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Impostare un punto di interruzione nel metodo `Initialize()` e avviare il debug (F5).  
  
5.  Aprire un progetto nell'istanza sperimentale. Il VSPackage verrà caricato e verrà raggiunto il punto di interruzione.  
  
 È possibile specificare altri contesti in cui caricare il VSPackage usando i campi di <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Per ulteriori informazioni, vedere [VSPackage durante il caricamento](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Come si recupera l'oggetto DTE?  
 Se il componente aggiuntivo non mostra un'interfaccia utente, ad esempio comandi di menu, pulsanti della barra degli strumenti o finestre degli strumenti, potrebbe essere possibile usare il codice così com'è purché si recuperi l'oggetto di automazione DTE dal VSPackage. Ecco come:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Per recuperare l'oggetto DTE da un VSPackage  
  
1.  In un progetto VSIX con un modello di elemento di pacchetto di Visual Studio, cercare il  *\<nome progetto >*Package.cs file. Si tratta della classe che deriva da <xref:Microsoft.VisualStudio.Shell.Package> e consente di interagire con Visual Studio. In questo caso, usare il relativo <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> per recuperare l'oggetto <xref:EnvDTE80.DTE2>.  
  
2.  Aggiungere queste istruzioni `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Trovare il metodo `Initialize`. Questo metodo gestisce i comandi specificati nella creazione guidata del pacchetto. Aggiungere una chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> per recuperare l'oggetto DTE:  
  
    ```csharp  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 Dopo avere recuperato l'oggetto di automazione <xref:EnvDTE.DTE>, è possibile aggiungere la parte rimanente del codice del componente aggiuntivo al progetto. Se occorre l'oggetto <xref:EnvDTE80.DTE2>, è possibile procedere nello stesso modo.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Come è possibile applicare lo stile del VSPackage ai comandi di menu e ai pulsanti della barra degli strumenti del componente aggiuntivo?  
 Le estensioni VSPackage usano il file con estensione vsct per creare la maggior parte dei comandi di menu, delle barre degli strumenti, dei pulsanti della barra degli strumenti e altri elementi dell'interfaccia utente. Il **comando personalizzato** il modello di elemento di progetto offre l'opzione per creare un comando sul **strumenti** menu. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Per ulteriori informazioni sui file con estensione vsct, vedere [come VSPackage aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Per procedure dettagliate che illustrano come utilizzare il file vsct per aggiungere voci di menu, barre degli strumenti e i pulsanti della barra degli strumenti, vedere [estensione menu e comandi](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Come è possibile aggiungere finestre degli strumenti personalizzate con lo stile del VSPackage?  
 Il modello di elemento di progetto finestra degli strumenti personalizzata offre l'opzione per creare una finestra degli strumenti. Per ulteriori informazioni su questo modello di elemento di progetto, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md). Per informazioni sulle finestre degli strumenti, vedere [estensione e le finestre degli strumenti personalizzazione](../extensibility/extending-and-customizing-tool-windows.md) e gli articoli, in particolare [aggiunta di una finestra degli strumenti](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Come è possibile gestire finestre di Visual Studio con lo stile del VSPackage?  
 Se il componente aggiuntivo gestisce le finestre di Visual Studio, il codice del componente aggiuntivo dovrebbe funzionare in un VSPackage. Ad esempio, questa procedura viene illustrato come aggiungere codice che gestisce il **elenco attività** per il `MenuItemCallback` (metodo) del pacchetto VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Per inserire il codice di gestione delle finestre da un componente aggiuntivo in un VSPackage  
  
1.  Creare un VSPackage che dispone di un comando di menu, come nel [come avviare lo sviluppo di estensioni VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sezione.  
  
2.  Aprire il file che contiene la definizione del VSPackage. (In un progetto c#, ha  *\<nome progetto >*Package.cs.)  
  
3.  Aggiungere queste istruzioni `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Trovare il metodo `MenuItemCallback`. Aggiungere una chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> per recuperare l'oggetto <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Aggiungere il codice dal componente aggiuntivo. Ad esempio, ecco alcuni codice che aggiunge nuove attività per il **elenco attività**Elenca il numero di attività e quindi elimina un'attività.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)   
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
        askItem tlItem;   
  
        // Add a couple of tasks to the Task List.   
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
            true, "", 10, true, true);  
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
        // List the total number of task list items after adding the new task items.  
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
        // Remove the second task item. The items list in reverse numeric order.   
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
        tl.TaskItems.Item(2).Delete();  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
    }  
    ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Come è possibile gestire progetti e soluzioni in un VSPackage?  
 Se il componente aggiuntivo gestisce progetti e soluzioni, il codice del componente aggiuntivo dovrebbe funzionare in un VSPackage. Questa procedura spiega come aggiungere il codice che ottiene il progetto di avvio.  
  
1.  Creare un VSPackage che dispone di un comando di menu, come nel [come avviare lo sviluppo di estensioni VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sezione.  
  
2.  Aprire il file che contiene la definizione del VSPackage. (In un progetto c#, ha  *\<nome progetto >*Package.cs.)  
  
3.  Aggiungere queste istruzioni `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Trovare il metodo `MenuItemCallback`. Aggiungere una chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> per recuperare l'oggetto <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Aggiungere il codice dal componente aggiuntivo. Nel codice seguente viene recuperato il nome del progetto di avvio in una soluzione. Durante l'esecuzione di questo pacchetto, deve essere aperta una soluzione multiprogetto.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
        Project startupProj;   
        string msg = "";  
  
        foreach (String item in (Array)sb.StartupProjects)   
        {  
            msg += item;   
        }  
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
        startupProj = dte.Solution.Item(msg);   
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
    }  
    ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Come è possibile impostare le scelte rapide da tastiera in un VSPackage?  
 È necessario usare l'elemento `<KeyBindings>` del file VSCT. Nell'esempio seguente la scelta rapida da tastiera per il comando `idCommand1` è ALT+A e la scelta rapida da tastiera per il comando `idCommand2` è ALT+CTRL+A. Osservare la sintassi per i nomi dei tasti.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Come è possibile gestire gli eventi di automazione in un VSPackage?  
 Gli eventi di automazione in un VSPackage e nel componente aggiuntivi vengono gestiti nello stesso modo. L'esempio di codice seguente mostra come gestire l'evento `OnItemRenamed`. In questo esempio si presuppone che l'oggetto DTE sia già stato recuperato.  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```