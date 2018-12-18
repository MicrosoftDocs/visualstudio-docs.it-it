---
title: Gestione dei progetti Windows universali | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d251818d9fba0c025b94fa17611a725daad3cec8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="managing-universal-windows-projects"></a>Gestione di progetti di Windows universale
App di Windows universale sono app di Windows 8.1 e Windows Phone 8.1, consentendo agli sviluppatori di utilizzare il codice e altre risorse in entrambe le piattaforme. Il codice condiviso e le risorse vengono mantenute in un progetto condiviso, mentre il codice specifico della piattaforma e le risorse vengono mantenute in progetti separati, uno per Windows e l'altro per Windows Phone. Per ulteriori informazioni sulle app di Windows universale, vedere [App Windows universali](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Estensioni di Visual Studio per la gestione di progetti devono essere consapevoli che i progetti di app Windows universali presentano una struttura diversa da una singola piattaforma App. Questa procedura dettagliata viene illustrato come passare al progetto condiviso e gestire gli elementi condivisi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Passare al progetto condiviso  
  
1.  Creare un progetto VSIX c# denominato **TestUniversalProject**. (**File, nuovo, progetto** e quindi **c#, estendibilità, il pacchetto di Visual Studio**). Aggiungi un **comando personalizzato** il modello di elemento di progetto (in Esplora soluzioni fare doppio clic sul nodo del progetto e selezionare **Aggiungi / nuovo elemento**, quindi passare alla **estendibilità**). Nome del file **TestUniversalProject**.  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll e Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (nel **estensioni** sezione).  
  
3.  Aprire TestUniversalProject.cs e aggiungere le seguenti `using` istruzioni:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  Nella classe TestUniversalProject aggiungere un campo privato scegliendo il **Output** finestra.  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Impostare il riferimento nel riquadro di output all'interno di TestUniversalProject costruttore:  
  
    ```csharp  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  
  
6.  Il codice esistente da rimuovere il `ShowMessageBox` metodo:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Ottiene l'oggetto DTE, che verrà utilizzato per scopi diversi in questa procedura dettagliata. Inoltre, assicurarsi che una soluzione venga caricata quando si fa clic sul pulsante di menu.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  
  
8.  Trovare il progetto condiviso. Progetto condiviso è un contenitore puro; non compilare o generare output. Il metodo seguente trova il primo progetto condiviso nella soluzione cercando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto che ha la possibilità di progetto condiviso.  
  
    ```csharp  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  
  
        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  
  
9. Nel `ShowMessageBox` (metodo), la didascalia di output (il nome del progetto che verrà visualizzato nel **Esplora**) del progetto condiviso.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  
  
10. Ottenere il progetto di piattaforma attiva. I progetti di piattaforma sono i progetti che contengono codice specifico della piattaforma e risorse. Il metodo seguente usa il nuovo campo <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> per ottenere il progetto di piattaforma attiva.  
  
    ```csharp  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  
  
11. Nel `ShowMessageBox` metodo, la didascalia del progetto di piattaforma attiva di output.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  
  
                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  
  
    ```  
  
12. Scorrere i progetti di piattaforma. Il metodo seguente ottiene tutti i progetti di (piattaforma) esegue l'importazione dal progetto condiviso.  
  
    ```csharp  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  Se l'utente ha aperto un progetto di app Windows universale C++ nell'istanza sperimentale, il codice precedente genera un'eccezione. Si tratta di un problema noto. Per evitare l'eccezione, sostituire il `foreach` blocco superiore con quanto segue:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. Nel `ShowMessageBox` metodo, la didascalia di ogni progetto della piattaforma di output. Inserire il codice seguente dopo la riga che genera la didascalia del progetto di piattaforma attiva. Solo i progetti di piattaforma che vengono caricati è visualizzata nell'elenco.  
  
    ```csharp  
    output.OutputStringThreadSafe("Platform projects:\n");  
  
    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  
  
    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  
  
14. Modificare il progetto di piattaforma attiva. Il metodo seguente imposta il progetto attivo utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. Nel `ShowMessageBox` (metodo), modificare il progetto di piattaforma attiva. Inserire il codice all'interno di `foreach` blocco.  
  
    ```csharp  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
  
        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  
  
16. Provare ora a eseguire l'operazione. Premere F5 per avviare l'istanza sperimentale. Creare un progetto di applicazione hub universale c# nell'istanza sperimentale (nel **nuovo progetto** nella finestra di dialogo **Visual c# / Windows / Windows 8 / Universal / App Hub**). Dopo il caricamento della soluzione, passare al **strumenti** menu e fare clic su **richiamare TestUniversalProject**, quindi selezionare il testo nel **Output** riquadro. Dovrebbe essere simile al seguente:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Gestire gli elementi condivisi nel progetto di piattaforma  
  
1.  Trovare gli elementi condivisi nel progetto di piattaforma. Gli elementi nel progetto condiviso vengono visualizzati nel progetto di piattaforma come gli elementi condivisi. Non è possibile visualizzarli nel **Esplora**, ma è possibile seguire la gerarchia di progetto per individuarli. Il metodo seguente illustra la gerarchia e raccoglie tutti gli elementi condivisi. Facoltativamente, viene restituita la didascalia di ogni elemento. Gli elementi condivisi sono identificati la nuova proprietà <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
    ```csharp  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  
  
        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  
  
        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
  
            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  
  
2.  Nel `ShowMessageBox` metodo, aggiungere il codice seguente per analizzare gli elementi di gerarchia del progetto di piattaforma. Inserirlo all'interno di `foreach` blocco.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Leggere gli elementi condivisi. Gli elementi condivisi vengono visualizzati nel progetto di piattaforma come file collegati nascosti, ed è possibile leggere tutte le proprietà come normali file collegati. Il seguente codice legge il percorso completo del primo elemento condiviso.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Provare ora a eseguire l'operazione. Premere F5 per avviare l'istanza sperimentale. Creare un progetto di applicazione hub universale c# nell'istanza sperimentale (nel **nuovo progetto** nella finestra di dialogo **Visual c# / Windows / Windows 8 / Universal / App Hub**) passare al **strumenti** menu e fare clic su **richiamare TestUniversalProject**, quindi selezionare il testo nel **Output** riquadro. Dovrebbe essere simile al seguente:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Il rilevamento delle modifiche nei progetti di piattaforma e progetti condivisi  
  
1.  È possibile utilizzare gli eventi di gerarchia e di progetto per rilevare le modifiche apportate in progetti condivisi, esattamente come per i progetti di piattaforma. Tuttavia, gli elementi del progetto nel progetto condiviso non sono visibili, il che significa che alcuni eventi non vengono attivati quando vengono modificati gli elementi di progetto condiviso.  
  
     Si consideri la sequenza di eventi quando viene rinominato un file in un progetto:  
  
    1.  Il nome del file è stato modificato su disco.  
  
    2.  Il file di progetto viene aggiornato per includere il nuovo nome del file.  
  
     Gli eventi di gerarchia (ad esempio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) in genere tenere traccia delle modifiche visualizzate nell'interfaccia utente, ad esempio il **Esplora soluzioni**. Gli eventi di gerarchia è consigliabile un'operazione di ridenominazione file costituita da un'operazione di eliminazione di file e quindi aggiunta di un file. Tuttavia, quando vengono modificati elementi invisibili, il sistema di eventi di gerarchia viene generato un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento ma non un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento. Di conseguenza, se si rinomina un file in un progetto di piattaforma, si otterrà sia <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ma se si rinomina un file in un progetto condiviso, è possibile ottenere solo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
     Per rilevare le modifiche negli elementi di progetto, è possibile gestire eventi di elemento di progetto DTE (quelli trovato <xref:EnvDTE.ProjectItemsEventsClass>). Tuttavia, se si sta gestendo un numero elevato di eventi, è possibile ottenere prestazioni migliori, gestione degli eventi in <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. In questa procedura dettagliata si mostrano solo gli eventi di gerarchia e gli eventi DTE. In questa procedura aggiungere un listener di eventi a un progetto condiviso, un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi che vengono generati per ogni operazione di ridenominazione.  
  
     In questa procedura aggiungere un listener di eventi a un progetto condiviso, un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi che vengono generati per ogni operazione di ridenominazione.  
  
2.  Aggiungere un listener di eventi. Aggiungere un nuovo file di classe al progetto e chiamarlo HierarchyEventListener.cs.  
  
3.  Aprire il file HierarchyEventListener.cs e aggiungere le seguenti istruzioni using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  Dispone il `HierarchyEventListener` implementa classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  Implementare i membri di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, come nel codice riportato di seguito.  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    {  
        private IVsHierarchy hierarchy;  
        IVsOutputWindowPane output;   
  
        internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
             this.hierarchy = hierarchy;  
             this.output = outputWindow;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
    }  
  
    ```  
  
6.  Nella stessa classe aggiungere un altro gestore eventi per l'evento DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, che si verifica ogni volta che viene rinominato un elemento di progetto.  
  
    ```csharp  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  Iscriversi per gli eventi di gerarchia. È necessario effettuare l'iscrizione separatamente per ogni progetto che si verifica. Aggiungere il codice seguente in `ShowMessageBox`, uno per il progetto condiviso, mentre l'altro per uno dei progetti della piattaforma.  
  
    ```csharp  
    // hook up the event listener for hierarchy events on the shared project  
    HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
    uint cookie1;  
    sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  
  
    // hook up the event listener for hierarchy events on the   
    active project  
    HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
    uint cookie2;  
    activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
    ```  
  
8.  Effettuare l'iscrizione per l'evento di elemento di progetto DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Aggiungere il codice seguente dopo che si collega un listener del secondo.  
  
    ```csharp  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. Modificare l'elemento condiviso. Non è possibile modificare gli elementi condivisi in un progetto di piattaforma. In alternativa, è necessario modificarli nel progetto condiviso che è il proprietario di questi elementi effettivi. È possibile ottenere l'ID di elemento corrispondente nel progetto condiviso con <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, fornendo il percorso completo dell'elemento condiviso. È quindi possibile modificare l'elemento condiviso. La modifica viene propagata per i progetti di piattaforma.  
  
    > [!IMPORTANT]
    >  È necessario verificare che sia o meno un elemento di progetto un elemento condiviso prima di modificarla.  
  
     Il metodo seguente modifica il nome di un file di elemento di progetto.  
  
    ```csharp  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  
  
10. Chiamare questo metodo dopo che tutto l'altro codice in `ShowMessageBox` per modificare il nome del file l'elemento nel progetto condiviso. Inserire questa istruzione dopo il codice che ottiene il percorso completo dell'elemento nel progetto condiviso.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Compilare ed eseguire il progetto. Creare un'applicazione hub universale c# nell'istanza sperimentale, passare al **strumenti** menu e fare clic su **TestUniversalProject richiamare**e controllare il testo nel riquadro di output generale. Il nome del primo elemento condiviso progetto (si presume che sia il file app. XAML) deve essere modificato e verificare che il <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> ha generato l'evento. In questo caso, poiché può causare App.xaml.cs da rinominare anche la ridenominazione di App. XAML, si dovrebbe quattro eventi (due per ogni progetto della piattaforma). (Eventi DTE non rilevare gli elementi nel progetto condiviso). Dovrebbe essere due <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> eventi (uno per ognuno dei progetti con piattaforma), ma non <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> eventi.  
  
12. Ora provare a rinominare un file in un progetto di piattaforma ed è possibile individuare la differenza tra gli eventi che vengono generate. Aggiungere il codice seguente in `ShowMessageBox` dopo la chiamata a `ModifyFileName`.  
  
    ```csharp  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. Compilare ed eseguire il progetto. Creare un progetto universale c# nell'istanza sperimentale, passare al **strumenti** menu e fare clic su **TestUniversalProject richiamare**e controllare il testo nel riquadro di output generale. Dopo che il file nel progetto di piattaforma viene rinominato, si otterranno entrambi un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento e un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento. Dopo aver modificato il file ha causato alcun altro file da modificare e poiché le modifiche apportate agli elementi in un progetto di piattaforma non ottenere propagate in qualsiasi punto, è solo uno di questi eventi.