---
title: Confronto tra oggetti MenuCommand e OleMenuCommands | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 
manager: douge
ms.openlocfilehash: 0465057549543d8e07742e3b3806ebdcab28eb28
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="menucommands-vs-olemenucommands"></a>Confronto tra oggetti MenuCommand e OleMenuCommand
È possibile creare comandi di menu derivandoli dall'oggetto <xref:System.ComponentModel.Design.MenuCommand> o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e implementando i gestori eventi appropriati. Nella maggior parte dei casi, è possibile usare <xref:System.ComponentModel.Design.MenuCommand>, come avviene nel modello di progetto VSPackage, ma talvolta potrebbe essere necessario usare <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 I comandi resi disponibili per l'IDE da un pacchetto VSPackage devono essere visibili e abilitati affinché un utente possa usarli. Quando i comandi vengono creati in un file VSCT usando il modello di progetto di pacchetto di Visual Studio, sono visibili e abilitati per impostazione predefinita. L'impostazione di alcuni flag dei comandi, ad esempio `DynamicItemStart`, può modificare il comportamento predefinito. È anche possibile modificare la visibilità, lo stato abilitato e altre proprietà di un comando nel codice in fase di esecuzione, accedendo all'oggetto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> associato al comando.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Posizioni dei modelli per il modello di pacchetto di Visual Studio  
 Il modello di pacchetto di Visual Studio è disponibile nella finestra di dialogo **Nuovo progetto** in **Visual Basic/Extensibility**, **C#/Extensibility**o **Altri tipi di progetto/Extensibility**.  
  
## <a name="creating-a-command"></a>Creazione di un comando  
 Tutti i comandi, i gruppi di comandi, i menu, le barre degli strumenti e le finestre degli strumenti sono definiti nel file VSCT. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Se si sta creando un pacchetto VSPackage usando il modello di pacchetto, selezionare **Comando di menu** per creare un file VSCT e definire un comando di menu predefinito. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Per aggiungere un comando all'IDE  
  
1.  Aprire il file VSCT.  
  
2.  Nella sezione `Symbols` individuare l'elemento [GuidSymbol](../extensibility/guidsymbol-element.md) che contiene i gruppi e i comandi.  
  
3.  Creare un elemento [IDSymbol](../extensibility/idsymbol-element.md) per ogni menu, gruppo o comando che si vuole aggiungere, come illustrato nell'esempio seguente.  
  
     <!--FIXME [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  -->
    ```xaml  
    <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
      <IDSymbol name="MyMenuGroup" value="0x1020" />
      <IDSymbol name="cmdidMyCommand" value="0x0100" />
    </GuidSymbol>
    ```  
  
    Gli attributi `name` degli elementi `GuidSymbol` e `IDSymbol` forniscono la coppia GUID:ID per ogni nuovo menu, gruppo o comando. L'oggetto `guid` rappresenta un set di comandi definito per il pacchetto VSPackage. È possibile definire più set di comandi. Ogni coppia GUID:ID deve essere univoca.  
  
4.  Nella sezione [Buttons](../extensibility/buttons-element.md) creare un elemento [Button](../extensibility/button-element.md) per definire il comando, come illustrato nell'esempio seguente.  
  
     <!--FIXME [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  -->
    ```xaml  
    <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```  
  
    1.  Impostare i campi `guid` e `id` in modo che corrispondano alla coppia GUID:ID del nuovo comando.  
  
    2.  Impostare l'attributo `priority` .  
  
         L'attributo `priority` viene usato dal file VSCT per determinare la posizione del pulsante tra gli altri oggetti nel gruppo padre.  
  
         I comandi con valori di priorità inferiore vengono visualizzati sopra i comandi che hanno valori di priorità superiore o a sinistra di essi. Sono consentiti valori di priorità identici, ma la posizione relativa dei comandi con uguale priorità è determinata dall'ordine di elaborazione dei pacchetti VSPackage in fase di esecuzione e tale ordine non può essere predeterminato.  
  
         Se l'attributo `priority` viene omesso, il suo valore viene impostato su 0.  
  
    3.  Impostare l'attributo `type` . Nella maggior parte dei casi, il suo valore sarà `"Button"`. Per le descrizioni di altri tipi di pulsanti validi, vedere [Button Element](../extensibility/button-element.md).  
  
5.  Nella definizione del pulsante creare un elemento [Strings](../extensibility/strings-element.md) che include un elemento [ButtonText](../extensibility/buttontext-element.md) per contenere il nome del menu come viene visualizzato nell'IDE e un elemento [CommandName](../extensibility/commandname-element.md) per contenere il nome del comando usato per accedere al menu nella finestra di  **comando**.  
  
     Se la stringa di testo del pulsante include il carattere "&", l'utente può aprire il menu premendo ALT più il carattere che segue immediatamente "&".  
  
     Se si aggiunge un elemento `Tooltip` , il testo contenuto verrà visualizzato quando l'utente passa il puntatore del mouse sul pulsante.  
  
6.  Aggiungere un elemento [Icon](../extensibility/icon-element.md) per specificare l'icona, se presente, da visualizzare con il comando. Le icone sono necessarie per i pulsanti sulle barre degli strumenti, ma non per le voci di menu. Gli oggetti `guid` e `id` dell'elemento `Icon` devono corrispondere a quelli di un elemento [Bitmap](../extensibility/bitmap-element.md) definito nella sezione `Bitmaps` .  
  
7.  Aggiungere flag dei comandi, come appropriato, per modificare l'aspetto e il comportamento del pulsante. A tale scopo, aggiungere un elemento [CommandFlag](../extensibility/command-flag-element.md) nella definizione del menu.  
  
8.  Impostare il gruppo padre del comando. Il gruppo padre può essere un gruppo che si crea, un gruppo di un altro pacchetto o un gruppo dell'IDE. Ad esempio, per aggiungere il comando sulla barra degli strumenti di modifica di Visual Studio, accanto ai pulsanti **Commento** e **Rimuovi commento** , impostare l'elemento padre su guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT. Se l'elemento padre è un gruppo definito dall'utente, deve essere il figlio di un menu, una barra degli strumenti o una finestra degli strumenti presente nell'IDE.  
  
     Per ottenere questo risultato sono disponibili due modi, a seconda della progettazione:  
  
    -   Nell'elemento `Button` creare un elemento [Parent](../extensibility/parent-element.md) e impostare i relativi campi `guid` e `id` sul GUID e sull'ID del gruppo che ospiterà il comando, noto anche come *gruppo padre primario*.  
  
         L'esempio seguente definisce un comando che verrà visualizzato in un menu definito dall'utente.  
  
         <!--FIXME [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  -->
        ```xaml  
        <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
          <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
          <Icon guid="guidImages" id="bmpPic1" />
          <Strings>
            <CommandName>cmdidTestCommand</CommandName>
            <ButtonText>Test Command</ButtonText>
          </Strings>
        </Button>
        ```  
  
    -   È possibile omettere l'elemento `Parent` se il comando deve essere posizionato usando un oggetto CommandPlacement. Creare un elemento [CommandPlacements](../extensibility/commandplacements-element.md) prima della sezione `Symbols` e aggiungere un elemento [CommandPlacement](../extensibility/commandplacement-element.md) con gli oggetti `guid` e `id` del comando, un oggetto `priority`e un elemento padre, come illustrato nell'esempio seguente.  
  
         <!-- FIXME [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)] -->  
        ```xaml  
        <CommandPlacements>
          <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
            <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
          </CommandPlacement>
        </CommandPlacements>
        ```  
  
         Se si creano più elementi CommandPlacement con la stessa coppia GUID:ID ed elementi padre diversi, un menu viene visualizzato in più posizioni. Per altre informazioni, vedere l'elemento [CommandPlacements](../extensibility/commandplacements-element.md) .  
  
     Per ulteriori informazioni sui gruppi di comandi e l'elemento padre, vedere [creazione riutilizzabile gruppi di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md).  
  
 A questo punto, il comando sarà visibile nell'IDE, ma non avrà alcuna funzionalità. Se il comando è stato creato dal modello di pacchetto, per impostazione predefinita avrà un gestore dell'evento Click che visualizza un messaggio.  
  
## <a name="handling-the-new-command"></a>Gestione del nuovo comando  
 La maggior parte dei comandi nel codice gestito può essere gestita dal framework di pacchetto gestito (MPF, Managed Package Framework) associando il comando a un oggetto <xref:System.ComponentModel.Design.MenuCommand> o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e implementando i relativi gestori eventi.  
  
 Per il codice che usa l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> direttamente per la gestione dei comandi, è necessario implementare l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e i relativi metodi. I due metodi più importanti sono <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Ottenere l'istanza di <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> , come illustrato nell'esempio seguente.  
  
     [!code-csharp[ButtonGroup#21](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  Creare un oggetto <xref:System.ComponentModel.Design.CommandID> che ha come parametri il GUID e l'ID del comando da gestire, come illustrato nell'esempio seguente.  
  
     [!code-csharp[ButtonGroup#22](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     Il modello di pacchetto di Visual Studio fornisce due raccolte, `GuidList` e `PkgCmdIDList`, per contenere GUID e ID dei comandi. Queste raccolte vengono popolate automaticamente per i comandi aggiunti dal modello, mentre per i comandi aggiunti manualmente è necessario aggiungere anche la voce relativa all'ID alla classe `PkgCmdIdList` .  
  
     In alternativa, è possibile popolare l'oggetto <xref:System.ComponentModel.Design.CommandID> usando il valore stringa non elaborato del GUID e il valore intero dell'ID.  
  
3.  Creare un'istanza di un oggetto <xref:System.ComponentModel.Design.MenuCommand> o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> che specifica il metodo che gestisce il comando insieme a <xref:System.ComponentModel.Design.CommandID>, come illustrato nell'esempio seguente.  
  
     [!code-csharp[ButtonGroup#23](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     L'oggetto <xref:System.ComponentModel.Design.MenuCommand> è appropriato per i comandi statici. Per la visualizzazione di voci di menu dinamiche, sono necessari gestori eventi QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> aggiunge l'evento <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> , che si verifica quando il menu host del comando viene aperto, e alcune altre proprietà, ad esempio <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     I comandi creati dal modello di pacchetto vengono passati per impostazione predefinita a un oggetto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nel metodo `Initialize()` della classe del pacchetto.  
  
4.  L'oggetto <xref:System.ComponentModel.Design.MenuCommand> è appropriato per i comandi statici. Per la visualizzazione di voci di menu dinamiche, sono necessari gestori eventi QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> aggiunge l'evento <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> , che si verifica quando il menu host del comando viene aperto, e alcune altre proprietà, ad esempio <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     I comandi creati dal modello di pacchetto vengono passati per impostazione predefinita a un oggetto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nel metodo `Initialize()` della classe del pacchetto. La procedura guidata di Visual Studio implementa il metodo `Initialize` usando `MenuCommand`. Per la visualizzazione delle voci di menu dinamiche, è necessario modificare questo elemento in `OleMenuCommand`, come illustrato nel passaggio successivo. Inoltre, per modificare il testo della voce di menu, è necessario aggiungere un flag di comando TextChanges al pulsante di comando del menu nel file VSCT, come illustrato nell'esempio seguente.  
  
     <!--FIXME [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]-->  
    ```xaml  
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
  
5.  Passare il nuovo comando di menu al metodo <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> nell'interfaccia <xref:System.ComponentModel.Design.IMenuCommandService> . Questa operazione viene eseguita per impostazione predefinita per i comandi creati dal modello di pacchetto, come illustrato nell'esempio seguente.  
  
     [!code-csharp[ButtonGroup#24](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  Implementare il metodo che gestisce il comando.  
  
#### <a name="to-implement-querystatus"></a>Per implementare QueryStatus  
  
1.  L'evento QueryStatus si verifica prima che un comando venga visualizzato. In questo modo, le proprietà di tale comando possono essere impostate nel gestore eventi prima che l'utente venga raggiunto. Solo i comandi aggiunti come oggetti <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> possono accedere a questo metodo.  
  
     Aggiungere un oggetto `EventHandler` all'evento <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> nell'oggetto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> creato per gestire il comando, come illustrato nell'esempio seguente (`menuItem` è l'istanza di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ).  
  
     [!code-csharp[MenuText#14](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
     [!code-vb[MenuText#14](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
     All'oggetto `EventHandler` viene assegnato il nome di un metodo che viene chiamato quando viene eseguita una query sullo stato del comando di menu.  
  
2.  Implementare il metodo del gestore dello stato di query per il comando. Il `object` `sender` parametro può essere convertito in un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> oggetto, che viene utilizzato per impostare i vari attributi del comando di menu, incluso il testo. La tabella seguente mostra le proprietà nella classe <xref:System.ComponentModel.Design.MenuCommand> (da cui deriva l'oggetto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> della classe MPF) che corrispondono ai flag <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> .  
  
    |Proprietà MenuCommand|Flag OLECMDF|  
    |--------------------------|------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
     Per modificare il testo di un comando di menu, usare la proprietà <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> nell'oggetto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , come illustrato nell'esempio seguente.  
  
     [!code-csharp[MenuText#11](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
     [!code-vb[MenuText#11](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
 Il framework MPF gestisce automaticamente il caso di gruppi non supportati o sconosciuti. A meno che un comando non sia stato aggiunto all'oggetto <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usando il metodo <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> , il comando non è supportato.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Gestione dei comandi usando l'interfaccia IOleCommandTarget  
 Per il codice che usa l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> direttamente, il pacchetto VSPackage deve implementare entrambi i metodi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> dell'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Se il pacchetto VSPackage implementa una gerarchia del progetto, devono invece essere implementati i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> dell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .  
  
 Entrambi i metodi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> sono progettati per ricevere un singolo oggetto `GUID` del set di comandi e una matrice di ID di comandi come input. È consigliabile che i pacchetti VSPackage supportino completamente questo concetto di ID multipli in una sola chiamata. Tuttavia, se il pacchetto VSPackage non viene chiamato da altri pacchetti VSPackage, è possibile presupporre che la matrice di comandi contenga un solo ID di comando perché i metodi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> vengono eseguiti in un ordine ben definito. Per ulteriori informazioni sul routing, vedere [comandi (Routing) in package VS](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Per il codice che usa l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> direttamente per la gestione dei comandi, è necessario implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> nel pacchetto VSPackage come illustrato di seguito per gestire i comandi.  
  
##### <a name="to-implement-the-querystatus-method"></a>Per implementare il metodo QueryStatus  
  
1.  Restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> per i comandi validi.  
  
2.  Impostare l'elemento `cmdf` del parametro `prgCmds` .  
  
     Il valore dell'elemento `cmdf` è l'unione logica dei valori dell'enumerazione <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> , combinati usando l'operatore logico OR (operatore`|`).  
  
     Usare l'enumerazione appropriata, in base allo stato del comando:  
  
    -   Se il comando è supportato:  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Se il comando deve essere invisibile al momento:  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Se il comando viene attivato e viene visualizzato come selezionato:  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         Nel caso di comandi di elaborazione ospitati in un menu di tipo `MenuControllerLatched`, il primo comando contrassegnato dal flag `OLECMDF_LATCHED` è il comando predefinito visualizzato dal menu all'avvio. Per altre informazioni sui tipi di menu `MenuController` , vedere [Menu Element](../extensibility/menu-element.md).  
  
    -   Se il comando è attualmente abilitato:  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Se il comando fa parte di un menu di scelta rapida ed è nascosto per impostazione predefinita:  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
    -   Se il comando usa il flag `TEXTCHANGES` , impostare l'elemento `rgwz` del parametro `pCmdText` sul nuovo testo del comando e impostare l'elemento `cwActual` del parametro `pCmdText` sulla dimensione della stringa di comando.  
  
     Per le condizioni di errore, il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> deve gestire i casi di errore seguenti:  
  
    -   Se il GUID è sconosciuto o non è supportato, restituire `OLECMDERR_E_UNKNOWNGROUP`.  
  
    -   Se il GUID è noto, ma l'ID di comando è sconosciuto o non è supportato, restituire `OLECMDERR_E_NOTSUPPORTED`.  
  
 L'implementazione del pacchetto VSPackage del metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> deve restituire anche codici di errore specifici, a seconda del fatto che il comando sia o meno supportato e che sia stato o meno gestito correttamente.  
  
##### <a name="to-implement-the-exec-method"></a>Per implementare il metodo Exec  
  
-   Se il comando `GUID` è sconosciuto, restituire `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Se il comando `GUID` è noto, ma l'ID di comando è sconosciuto, restituire `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Se `GUID` e ID di comando corrispondono alla coppia GUID:ID usata dal comando nel file VSCT, eseguire il codice associato al comando e restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)