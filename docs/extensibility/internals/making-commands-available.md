---
title: Rendere disponibili i comandi | Documenti Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e20fd9b1b13dfc8159181ee2cb8f5d8966f6faf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="making-commands-available"></a>Rendere disponibili i comandi
Quando più VSPackage vengono aggiunti a Visual Studio, l'interfaccia utente (UI) potrebbe diventare saturi con i comandi. È possibile programmare il pacchetto per ridurre questo problema, come indicato di seguito:

-   Il pacchetto di programma in modo che viene caricato solo quando un utente richiede.

-   Programmare il pacchetto in modo che i comandi vengono visualizzati solo quando potrebbero essere necessari nel contesto dello stato corrente dell'ambiente di sviluppo integrato (IDE).

## <a name="delayed-loading"></a>Caricamento ritardato
 Il modo comune per abilitare il caricamento ritardato consiste nel progettare il pacchetto VSPackage in modo che i comandi vengono visualizzati nell'interfaccia utente, ma il pacchetto non verrà caricato finché un utente fa clic su uno dei comandi. A tale scopo, nel file vsct, creare i comandi che non dispongono di alcun flag dei comandi.

 Nell'esempio seguente viene illustrata la definizione di un comando di menu da un file con estensione vsct. Questo è il comando che viene generato per il modello di pacchetto di Visual Studio quando il **comando di Menu** è selezionata l'opzione nel modello.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>

```

 Nell'esempio, se il gruppo padre, `MyMenuGroup`, è un figlio di un menu di primo livello, ad esempio il **strumenti** menu, il comando sarà visibile nel menu, ma il pacchetto che esegue il comando non verrà caricato finché non si seleziona il comando da un utente. Tuttavia, se il comando per l'implementazione di programmazione il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, è possibile abilitare il pacchetto da caricare quando il menu che contiene il comando viene espanso.

 Si noti che il caricamento ritardato di migliorare le prestazioni all'avvio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contesto corrente e la visibilità dei comandi
 È possibile eseguire i comandi di VSPackage per essere visualizzate o nascoste, a seconda dello stato corrente dei dati VSPackage o le azioni che sono attualmente rilevanti. È possibile abilitare il pacchetto VSPackage impostare lo stato dei comandi, in genere tramite un'implementazione del <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, ma questo richiede il pacchetto VSPackage deve essere caricato prima di poter eseguire il codice. È invece consigliabile abilitare l'IDE gestire la visibilità dei comandi senza il caricamento del pacchetto. A tale scopo, nel file vsct, associare i comandi di uno o più contesti dell'interfaccia utente speciale. Questi contesti dell'interfaccia utente sono identificati da un GUID noto come un *il GUID di contesto di comando*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Consente di monitorare le modifiche risultanti da azioni dell'utente, ad esempio il caricamento di un progetto o verrà dalla modifica di compilazione. Quando si verificano modifiche, viene modificato automaticamente l'aspetto dell'IDE. Nella tabella seguente mostra quattro principali contesti dell'IDE di modifica che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitoraggi.

|Tipo di contesto|Descrizione|
|---------------------|-----------------|
|Tipo di progetto attivo|Per la maggior parte dei tipi di progetto, questo `GUID` valore corrisponde al GUID del pacchetto VSPackage che implementa il progetto. Tuttavia, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti utilizzano il tipo di progetto `GUID` come valore.|
|Finestra attiva|In genere, questo è l'ultima finestra di documento che definisce il contesto corrente dell'interfaccia utente per i tasti di scelta rapida. Tuttavia, potrebbe anche essere una finestra degli strumenti che dispone di una tabella di tasti che è simile al browser interno. Per le finestre di documento a schede, ad esempio l'editor HTML, ogni scheda dispone di un contesto di comandi diversi `GUID`.|
|Servizio di linguaggio Active|Il servizio di linguaggio che è associato al file che è attualmente visualizzato in un editor di testo.|
|Finestra degli strumenti attiva|Una finestra degli strumenti è aperto e ha lo stato attivo.|

 Un'area principale contesto quinto è lo stato dell'interfaccia utente dell'IDE. Contesti dell'interfaccia utente sono identificati dal contesto del comando attivo `GUID`s, come indicato di seguito:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

 Questi GUID sono contrassegnati come attivo o inattivo, a seconda dello stato corrente dell'IDE. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Nascondere e visualizzare i comandi in base al contesto
 È possibile visualizzare o nascondere un comando di pacchetto nell'IDE senza caricare il pacchetto stesso. A tale scopo, definire il comando nel file vsct del pacchetto tramite il `DefaultDisabled`, `DefaultInvisible`, e `DynamicVisibility` comando flag e aggiungere uno o più [VisibilityItem](../../extensibility/visibilityitem-element.md) elementi per il [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sezione. Quando un contesto di comando specificato `GUID` diventa attivo, il comando viene visualizzato senza il caricamento del pacchetto.

### <a name="custom-context-guids"></a>GUID di contesto personalizzato
 Se GUID non è già stato definito un contesto di comando appropriato, è possibile definire uno nel pacchetto VSPackage e programmarlo per essere attivi o inattivi come richiesto per controllare la visibilità dei comandi. Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio:

-   Registra i GUID di contesto (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (metodo)).

-   Ottenere lo stato di un contesto `GUID` (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (metodo)).

-   Contesto di attivazione `GUID`s e disattiva (chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (metodo)).

    > [!CAUTION]
    > Assicurarsi che il pacchetto VSPackage non influiscono sullo stato di qualsiasi GUID di contesto esistente perché altri pacchetti VSPackage potrebbe dipendere da essi.

## <a name="example"></a>Esempio
 L'esempio seguente di un comando di VSPackage illustra la visibilità dinamica di un comando che è gestito da contesti di comando senza caricare il pacchetto VSPackage.

 Il comando è impostato per essere abilitato e visualizzata ogni volta che una soluzione esistente; ovvero, ogni volta che uno del contesto del comando seguente GUID è attivo:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>

Nell'esempio, si noti che ogni flag di comando è un oggetto separato [Flag di comando](../../extensibility/command-flag-element.md) elemento.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Si noti anche che ogni contesto dell'interfaccia utente deve essere specificato in un apposito `VisibilityItem` elemento, come indicato di seguito.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Vedere anche

- [Confronto tra oggetti MenuCommand e OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Aggiunta dinamica di voci di menu](../../extensibility/dynamically-adding-menu-items.md)