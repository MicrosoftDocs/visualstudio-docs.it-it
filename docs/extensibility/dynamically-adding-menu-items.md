---
title: Aggiunta dinamica di voci di menu | Microsoft Docs
description: Informazioni su come usare il flag di comando DynamicItemStart per aggiungere voci di menu in fase di esecuzione. Questo articolo illustra come impostare il progetto di avvio in una soluzione di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa85d5b5cf4b99840e181fb24b5913ff72a3fee0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070336"
---
# <a name="dynamically-add-menu-items"></a>Aggiungi dinamicamente voci di menu
È possibile aggiungere voci di menu in fase di esecuzione specificando il `DynamicItemStart` flag di comando in una definizione di pulsante segnaposto nel file della tabella dei comandi di Visual Studio (con *estensione vsct*), quindi definendo (in codice) il numero di voci di menu da visualizzare e gestire i comandi. Quando si carica il pacchetto VSPackage, il segnaposto viene sostituito con le voci di menu dinamiche.

 Visual Studio usa gli elenchi dinamici nell'elenco degli **ultimi elementi usati** (MRU), che Visualizza i nomi dei documenti aperti di recente, e l'elenco di **Windows** , che Visualizza i nomi delle finestre attualmente aperte.   Il `DynamicItemStart` flag in una definizione di comando specifica che il comando è un segnaposto fino all'apertura del pacchetto VSPackage. Quando si apre il pacchetto VSPackage, il segnaposto viene sostituito con 0 o più comandi creati in fase di esecuzione e aggiunti all'elenco dinamico. Potrebbe non essere possibile visualizzare la posizione nel menu in cui viene visualizzato l'elenco dinamico fino a quando non viene aperto il pacchetto VSPackage.  Per popolare l'elenco dinamico, Visual Studio chiede al VSPackage di cercare un comando con un ID i cui primi caratteri corrispondano all'ID del segnaposto. Quando Visual Studio trova un comando corrispondente, aggiunge il nome del comando all'elenco dinamico. Incrementa quindi l'ID e cerca un altro comando corrispondente da aggiungere all'elenco dinamico fino a quando non sono presenti altri comandi dinamici.

 Questa procedura dettagliata illustra come impostare il progetto di avvio in una soluzione di Visual Studio con un comando sulla barra degli strumenti **Esplora soluzioni** . Usa un controller di menu che dispone di un elenco a discesa dinamico dei progetti nella soluzione attiva. Per evitare che questo comando venga visualizzato quando nessuna soluzione è aperta o quando la soluzione aperta ha un solo progetto, il pacchetto VSPackage viene caricato solo quando una soluzione contiene più progetti.

 Per ulteriori informazioni sui file con *estensione vsct* , vedere [file di tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menu

1. Creare un progetto VSIX denominato `DynamicMenuItems` .

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato e denominarlo **DynamicMenu**. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Impostazione degli elementi nel file con *estensione vsct*
 Per creare un controller di menu con voci di menu dinamiche su una barra degli strumenti, è necessario specificare gli elementi seguenti:

- Due gruppi di comandi, uno contenente il controller di menu e un altro che contiene le voci di menu nell'elenco a discesa

- Un elemento di menu di tipo `MenuController`

- Due pulsanti, uno che funge da segnaposto per le voci di menu e un altro che fornisce l'icona e la descrizione comando sulla barra degli strumenti.

1. In *DynamicMenuPackage. vsct*, definire gli ID dei comandi. Passare alla sezione simboli e sostituire gli elementi IDSymbol nel blocco **guidDynamicMenuPackageCmdSet** GuidSymbol. È necessario definire gli elementi IDSymbol per i due gruppi, il controller di menu, il comando segnaposto e il comando di ancoraggio.

    ```xml
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

2. Nella sezione gruppi eliminare i gruppi esistenti e aggiungere i due gruppi appena definiti:

    ```xml
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

     Aggiungere MenuController. Impostare il flag di comando DynamicVisibility, poiché non è sempre visibile. ButtonText non viene visualizzato.

    ```xml
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

3. Aggiungere due pulsanti, uno come segnaposto per le voci di menu dinamico e uno come ancoraggio per MenuController.

     L'elemento padre del pulsante segnaposto è **MyMenuControllerGroup**. Aggiungere i flag di comando DynamicItemStart, DynamicVisibility e TEXTCHANGES al al pulsante segnaposto. ButtonText non viene visualizzato.

     Il pulsante di ancoraggio include l'icona e il testo della descrizione comando. Anche l'elemento padre del pulsante di ancoraggio è **MyMenuControllerGroup**. Si aggiunge il flag di comando NoShowOnMenuController per verificare che il pulsante non sia effettivamente visualizzato nell'elenco a discesa del controller di menu e il flag di comando FixMenuController per impostarlo come ancoraggio permanente.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
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

4. Aggiungere un'icona al progetto (nella cartella *Resources* ), quindi aggiungere il riferimento al file con *estensione vsct* . In questa procedura dettagliata viene usata l'icona delle frecce inclusa nel modello di progetto.

5. Aggiungere una sezione VisibilityConstraints all'esterno della sezione commands immediatamente prima della sezione dei simboli. È possibile che venga visualizzato un avviso se viene aggiunto dopo i simboli. In questa sezione si garantisce che il controller di menu venga visualizzato solo quando viene caricata una soluzione con più progetti.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementare il comando di menu dinamico
 Si crea una classe di comando di menu dinamico che eredita da <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> . In questa implementazione, il costruttore specifica un predicato da usare per i comandi corrispondenti. È necessario eseguire l'override del <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodo per utilizzare questo predicato per impostare la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> proprietà, che identifica il comando da richiamare.

1. Creare un nuovo file di classe C# denominato *DynamicItemMenuCommand. cs* e aggiungere una classe denominata **DynamicItemMenuCommand** che eredita da <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Aggiungere le seguenti direttive using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Aggiungere un campo privato per archiviare il predicato di corrispondenza:

    ```csharp
    private Predicate<int> matches;

    ```

4. Aggiungere un costruttore che erediti dal <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> costruttore e specifichi un gestore di comando e un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore. Aggiungere un predicato per la corrispondenza del comando:

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

5. Eseguire l'override del <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodo in modo che chiami il predicato Matches e imposta la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> proprietà:

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

## <a name="add-the-command"></a>Aggiungere il comando
 Il costruttore DynamicMenu è la posizione in cui vengono impostati i comandi di menu, inclusi i menu dinamici e le voci di menu.

1. In *DynamicMenuPackage. cs* aggiungere il GUID del set di comandi e l'ID del comando:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Nel file *DynamicMenu. cs* aggiungere le direttive using seguenti:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Nella `DynamicMenu` classe aggiungere un campo privato **DTE2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Aggiungere un campo rootItemId privato:

    ```csharp
    private int rootItemId = 0;
    ```

5. Nel costruttore DynamicMenu aggiungere il comando di menu. Nella sezione successiva si definiranno il gestore di comandi, il `BeforeQueryStatus` gestore eventi e il predicato di corrispondenza.

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

## <a name="implement-the-handlers"></a>Implementare i gestori
 Per implementare voci di menu dinamiche in un controller di menu, è necessario gestire il comando quando si fa clic su un elemento dinamico. È inoltre necessario implementare la logica che imposta lo stato della voce di menu. Aggiungere i gestori alla `DynamicMenu` classe.

1. Per implementare il comando **set Startup Project** , aggiungere il gestore dell'evento **OnInvokedDynamicItem** . Cerca il progetto il cui nome è lo stesso del testo del comando che è stato richiamato e lo imposta come progetto di avvio impostando il relativo percorso assoluto nella <xref:EnvDTE.SolutionBuild.StartupProjects%2A> Proprietà.

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

2. Aggiungere il `OnBeforeQueryStatusDynamicItem` gestore eventi. Si tratta del gestore chiamato prima di un `QueryStatus` evento. Determina se la voce di menu è un elemento "reale", ovvero non l'elemento segnaposto, e se l'elemento è già selezionato (ovvero se il progetto è già impostato come progetto di avvio).

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

## <a name="implement-the-command-id-match-predicate"></a>Implementare il predicato di corrispondenza ID comando

Implementare ora il predicato di corrispondenza. È necessario determinare due elementi: prima di tutto, se l'ID del comando è valido (è maggiore o uguale all'ID di comando dichiarato) e secondo, se specifica un progetto possibile (è minore del numero di progetti nella soluzione).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Impostare il pacchetto VSPackage per il caricamento solo quando una soluzione include più progetti
 Poiché il comando **Imposta progetto di avvio** non ha senso, a meno che la soluzione attiva non disponga di più di un progetto, è possibile impostare il pacchetto VSPackage per il caricamento automatico solo in questo caso. Usare <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> insieme al contesto dell'interfaccia utente <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> . Nel file *DynamicMenuPackage. cs* aggiungere gli attributi seguenti alla classe DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testare il comando imposta progetto di avvio
 A questo punto è possibile testare il codice.

1. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

2. Nell'istanza sperimentale aprire una soluzione con più di un progetto.

     Verrà visualizzata l'icona freccia sulla barra degli strumenti **Esplora soluzioni** . Quando si espande il progetto, verranno visualizzate le voci di menu che rappresentano i diversi progetti della soluzione.

3. Quando si seleziona uno dei progetti, diventa il progetto di avvio.

4. Quando si chiude la soluzione o si apre una soluzione con un solo progetto, l'icona della barra degli strumenti dovrebbe scomparire.

## <a name="see-also"></a>Vedi anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
