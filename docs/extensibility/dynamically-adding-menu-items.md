---
title: Aggiunta di voci di Menu dinamicamente | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1eaa8cc41e7b27d509e68d6785c34a9ae214ffd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="dynamically-adding-menu-items"></a>Aggiunta dinamica di voci di Menu
È possibile aggiungere voci di menu in fase di esecuzione, specificando il `DynamicItemStart` comando flag su una definizione di pulsante segnaposto nel file di comando-table (vsct) di Visual Studio, quindi definire (nel codice) il numero di menu degli elementi da visualizzare e gestire i comandi. Quando viene caricato il pacchetto VSPackage, il segnaposto viene sostituito con le voci di menu dinamico.  
  
 Visual Studio Usa elenchi dinamici nel **usati di recente** elenco (MRU), che visualizza i nomi dei documenti aperti di recente, e **Windows** elenco, che visualizza i nomi di windows che sono attualmente aperti.   Il `DynamicItemStart` flag in una definizione di comando specifica che il comando è un segnaposto finché non viene aperto il pacchetto VSPackage. Quando il pacchetto VSPackage è aperto, il segnaposto viene sostituito con 0 o altri comandi che vengono creati in fase di esecuzione e aggiunto all'elenco dinamico. Potrebbe non essere in grado di visualizzare la posizione del menu in cui viene visualizzato l'elenco dinamico finché non viene aperto il pacchetto VSPackage.  Per popolare l'elenco dinamico, Visual Studio chiede il pacchetto VSPackage per cercare un comando con un ID i cui primi caratteri sono le stesse l'ID del segnaposto. Quando Visual Studio rileva che un comando corrispondente, aggiunge il nome del comando all'elenco dinamico. Incrementa l'ID ed esegue la ricerca di un altro comando corrispondente da aggiungere all'elenco dinamico, fino a quando non sono disponibili i comandi non più dinamici.  
  
 Questa procedura dettagliata viene illustrato come impostare il progetto di avvio in una soluzione di Visual Studio con un comando per il **Esplora** barra degli strumenti. Usa un controller di menu che contiene un elenco a discesa dinamica dei progetti nella soluzione attiva. Per evitare che questo comando che viene visualizzato quando nessuna soluzione è aperta o quando la soluzione aperta ha un solo progetto, il pacchetto VSPackage viene caricato solo quando una soluzione con più progetti.  
  
 Per ulteriori informazioni sui file con estensione vsct, vedere [Visual Studio Command Table (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Creazione di un'estensione con un comando di Menu  
  
1.  Creare un progetto VSIX denominato `DynamicMenuItems`.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato e denominarla **DynamicMenu**. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Impostazione degli elementi nel file vsct  
 Per creare un controller di menu con voci di menu dinamico in una barra degli strumenti, specificare gli elementi seguenti:  
  
-   Due gruppi, uno che contiene il controller di menu e un altro che contiene le voci di menu a discesa di comando  
  
-   Elemento di un menu di tipo`MenuController`  
  
-   Due pulsanti, uno che funge da segnaposto per le voci di menu e un altro che fornisce l'icona e la descrizione comando sulla barra degli strumenti.  
  
1.  In DynamicMenuPackage.vsct, è possibile definire gli ID di comando. Passare alla sezione simboli e sostituire gli elementi IDSymbol il **guidDynamicMenuPackageCmdSet** GuidSymbol blocco. È necessario definire gli elementi IDSymbol per i due gruppi, il controller di menu, il comando di segnaposto e il comando di ancoraggio.  
  
    ```csharp  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  Nella sezione gruppi, eliminare i gruppi esistenti e aggiungere i due gruppi che appena definito:  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     Aggiungere il MenuController. Impostare il flag di comando DynamicVisibility, perché non è sempre visibile. Non viene visualizzato il ButtonText.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Aggiungere due pulsanti, uno come segnaposto per le voci di menu dinamico e come un ancoraggio per il MenuController.  
  
     L'elemento padre del pulsante segnaposto è il **MyMenuControllerGroup**. Aggiungere i flag di comando DynamicItemStart DynamicVisibility e testoConsente di modificare il pulsante di segnaposto. Non viene visualizzato il ButtonText.  
  
     Il pulsante di ancoraggio contiene l'icona e il testo della descrizione comando. L'elemento padre del pulsante di ancoraggio è anche il **MyMenuControllerGroup**. Aggiungere il flag di comando NoShowOnMenuController per assicurarsi che il pulsante non compare effettivamente nel controller di menu a discesa e il flag di comando FixMenuController per renderlo permanente ancoraggio.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Aggiungere un'icona al progetto (nella cartella delle risorse) e quindi aggiungere il riferimento a esso nel file vsct. In questa procedura dettagliata, è utilizzare l'icona di frecce che è incluso nel modello di progetto.  
  
5.  Aggiungere una sezione VisibilityConstraints all'esterno della sezione comandi appena prima della sezione di simboli. (È possibile ricevere un avviso se aggiunti dopo i simboli). In questa sezione assicura che il controller di menu viene visualizzata solo quando viene caricata una soluzione con più progetti.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Implementazione del comando di menu dinamico  
 Creare una classe di comando di menu dinamico che eredita da <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. In questa implementazione, il costruttore viene specificato un predicato da utilizzare per la corrispondenza di comandi. È necessario eseguire l'override di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodo da utilizzare il predicato per impostare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> proprietà che identifica il comando da richiamare.  
  
1.  Creare un nuovo file classe c# denominato DynamicItemMenuCommand.cs e aggiungere una classe denominata **DynamicItemMenuCommand** che eredita da <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Aggiungere le seguenti istruzioni using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Aggiungere un campo privato per archiviare il predicato di corrispondenza:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Aggiungere un costruttore che eredita il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> costruttore e specifica un gestore del comando e un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore. Aggiungere un predicato per il comando corrispondente:  
  
    ```csharp  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Eseguire l'override di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodo in modo che venga chiamato le corrispondenze di predicato e imposta il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> proprietà:  
  
    ```csharp  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## <a name="adding-the-command"></a>Aggiunge il comando  
 Il costruttore di DynamicMenu è in cui impostare i comandi di menu, menu dinamici e voci di menu.  
  
1.  In DynamicMenuPackageGuids.cs, aggiungere il GUID del set di comandi e l'ID di comando:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  Nel file DynamicMenu.cs, aggiungere le seguenti istruzioni using:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Nella classe DynamicMenu, aggiungere un campo privato **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Aggiungere un campo privato rootItemId:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  Nel costruttore DynamicMenu, aggiungere il comando di menu. Nella sezione successiva definiamo il gestore del comando, il `BeforeQueryStatus` gestore dell'evento e il predicato di corrispondenza.  
  
    ```csharp  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## <a name="implementing-the-handlers"></a>I gestori di implementazione  
 Per implementare le voci di menu dinamico in un controller di menu, è necessario gestire il comando quando si fa clic su un elemento dinamico. È inoltre necessario implementare la logica che imposta lo stato della voce di menu. Aggiungere i gestori per la classe DynamicMenu.  
  
1.  Per implementare il **Imposta progetto di avvio** comando, aggiungere il **OnInvokedDynamicItem** gestore dell'evento. Cerca il progetto, il cui nome corrisponde al testo del comando che è stato richiamato e la imposta come progetto di avvio, impostando il relativo percorso assoluto nella <xref:EnvDTE.SolutionBuild.StartupProjects%2A> proprietà.  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don't need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Aggiungere il `OnBeforeQueryStatusDynamicItem` gestore dell'evento. Questo è il gestore chiamato prima che un `QueryStatus` evento. Determina se la voce di menu è un elemento "real", vale a dire, non l'elemento segnaposto, e se l'elemento è già selezionato (vale a dire che il progetto è già impostato come progetto di avvio).  
  
    ```csharp  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## <a name="implementing-the-command-id-match-predicate"></a>Implementare il predicato di corrispondenza ID di comando  
  
1.  A questo punto implementare il predicato di corrispondenza. È necessario determinare due elementi: innanzitutto, se l'ID di comando è valido (è maggiore o uguale all'ID di comando dichiarato) e il secondo se specifica un progetto possibile (è inferiore al numero di progetti nella soluzione).  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Impostare il pacchetto VSPackage di caricare solo quando una soluzione con più progetti  
 Poiché il **Imposta progetto di avvio** comando non ha senso solo se la soluzione attiva include più di un progetto, è possibile impostare il pacchetto VSPackage per caricare automaticamente solo in questo caso. Utilizzare <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> con il contesto dell'interfaccia utente <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. Nel file DynamicMenuPackage.cs aggiungere gli attributi seguenti alla classe DynamicMenuPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>Il comando Imposta progetto di avvio di test  
 È ora possibile testare il codice.  
  
1.  Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.  
  
2.  Nell'istanza sperimentale, aprire una soluzione che include più di un progetto.  
  
     Nella verrà visualizzata l'icona di freccia di **Esplora** barra degli strumenti. Quando si espande, voci di menu che rappresentano i diversi progetti nella soluzione dovrebbero essere visualizzato.  
  
3.  Quando si seleziona uno dei progetti, diventa il progetto di avvio.  
  
4.  Quando si chiude la soluzione o apre una soluzione che include un solo progetto, l'icona della barra degli strumenti deve essere nascosto.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)