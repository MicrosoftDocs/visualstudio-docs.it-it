---
title: La creazione. File Vsct | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65fc62d5685ca7c81b3ebb7f524db3cdbebe72c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="authoring-vsct-files"></a>La creazione. File Vsct
Questo documento viene illustrato come creare un file vsct per aggiungere voci di menu, barre degli strumenti e altri elementi dell'interfaccia utente per l'ambiente di sviluppo integrato (IDE) di Visual Studio. Utilizzare questa procedura quando si aggiungono elementi dell'interfaccia utente a un pacchetto di Visual Studio (VSPackage) che non dispone già di un file con estensione vsct.  
  
 Per i nuovi progetti, è consigliabile utilizzare il modello di pacchetto di Visual Studio in quanto genera un file con estensione vsct che, a seconda delle selezioni, già gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato. È possibile modificare questo file con estensione vsct per soddisfare i requisiti di un VSPackage. Per ulteriori informazioni su come modificare un file vsct, vedere gli esempi in [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>La creazione del File  
 L'autore di un file vsct in queste fasi: creazione della struttura di file e risorse, dichiarare gli elementi dell'interfaccia utente, inserire gli elementi dell'interfaccia utente nell'IDE e aggiungere eventuali comportamenti specializzati.  
  
### <a name="file-structure"></a>Struttura dei file  
 La struttura di base di un file con estensione vsct è un [CommandTable](../../extensibility/commandtable-element.md) elemento radice che contiene un [comandi](../../extensibility/commands-element.md) elemento e un [simboli](../../extensibility/symbols-element.md) elemento.  
  
##### <a name="to-create-the-file-structure"></a>Per creare la struttura di file  
  
1.  Aggiungere al progetto un file con estensione vsct seguendo i passaggi descritti in [procedura: creare una. Il File Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Aggiungere gli spazi dei nomi necessari per il `CommandTable` elemento, come illustrato nell'esempio seguente.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  Nel `CommandTable` elemento, aggiungere un `Commands` elemento per ospitare tutti i menu personalizzati, barre degli strumenti, i gruppi di comandi e i comandi. In modo che sia possono caricare elementi dell'interfaccia utente personalizzati, il `Commands` l'elemento deve avere il relativo `Package` attributo impostato sul nome del pacchetto.  
  
     Dopo il `Commands` elemento, aggiungere un `Symbols` elemento per definire i GUID per il pacchetto e i nomi e ID di comando per gli elementi dell'interfaccia utente.  
  
### <a name="including-visual-studio-resources"></a>L'inclusione di risorse di Visual Studio  
 Utilizzare il [Extern](../../extensibility/extern-element.md) elemento per accedere ai file che definiscono i comandi di Visual Studio e i menu necessari per inserire elementi dell'interfaccia utente nell'IDE. Se si utilizzeranno comandi definiti all'esterno del pacchetto, utilizzare il [UsedCommands](../../extensibility/usedcommands-element.md) elemento per informare Visual Studio.  
  
##### <a name="to-include-visual-studio-resources"></a>Per includere risorse di Visual Studio  
  
1.  Nella parte superiore del `CommandTable` elemento, aggiungere uno `Extern` elemento per ogni file esterni da cui viene fatto riferimento e impostare il `href` attributo per il nome del file. È possibile fare riferimento i seguenti file di intestazione per accedere alle risorse di Visual Studio:  
  
    -   Stdidcmd.h, definisce gli ID per tutti i comandi esposti da Visual Studio.  
  
    -   Vsshlids.h, contiene l'ID di comando per il menu di Visual Studio.  
  
2.  Se il pacchetto chiama i comandi che sono definiti da Visual Studio o da altri pacchetti, aggiungere un `UsedCommands` elemento dopo il `Commands` elemento. Questo elemento popolato con un [UsedCommand](../../extensibility/usedcommand-element.md) elemento per ogni comando, vale a dire chiamare non fa parte del pacchetto. Impostare il `guid` e `id` gli attributi del `UsedCommand` elementi ai valori GUID e ID dei comandi per chiamare. Per ulteriori informazioni su come individuare i comandi i GUID e ID di Visual Studio, vedere [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Per chiamare i comandi da altri pacchetti, utilizzare il GUID e l'ID del comando, come definito nel file vsct per tali pacchetti.  
  
### <a name="declaring-ui-elements"></a>Dichiarazione di elementi dell'interfaccia utente  
 Tutti i nuovi elementi dell'interfaccia utente di dichiarare il `Symbols` sezione del file con estensione vsct.  
  
##### <a name="to-declare-ui-elements"></a>Per dichiarare gli elementi dell'interfaccia utente  
  
1.  Nel `Symbols` elemento, aggiungere tre [GuidSymbol](../../extensibility/guidsymbol-element.md) elementi. Ogni `GuidSymbol` elemento ha un `name` attributo e un `value` attributo. Impostare il `name` attributo in modo che rifletta lo scopo dell'elemento. Il `value` attributo accetta un GUID. (Per generare un GUID, nel **strumenti** menu, fare clic su **Crea GUID**e quindi selezionare **il formato del Registro di sistema**.)  
  
     Il primo `GuidSymbol` elemento rappresenta il pacchetto e in genere non ha elementi figlio. Il secondo `GuidSymbol` elemento rappresenta il comando set e conterrà tutti i simboli che definiscono i menu, gruppi e i comandi. Il terzo `GuidSymbol` elemento rappresenta l'archivio di immagini e contiene i simboli per tutte le icone per i comandi. Se non si dispone di alcun comando che utilizzano le icone, è possibile omettere il terzo `GuidSymbol` elemento.  
  
2.  Nel `GuidSymbol` elemento che rappresenta il set di comandi, aggiungere uno o più [IDSymbol](../../extensibility/idsymbol-element.md) elementi. Ciascuno di questi rappresenta un menu, sulla barra degli strumenti, gruppo o comando per aggiungere l'interfaccia utente.  
  
     Per ogni `IDSymbol` elemento, impostare il `name` attributo per il nome verrà utilizzato per fare riferimento al menu corrispondente, gruppo o comando e quindi impostare il `value` elemento in un numero esadecimale che rappresenta l'id di comando. Nessun due `IDSymbol` gli elementi che hanno lo stesso elemento padre possono avere lo stesso valore.  
  
3.  Se uno qualsiasi degli elementi dell'interfaccia utente richiede le icone, aggiungere un `IDSymbol` elemento per ogni icona per il `GuidSymbol` elemento che rappresenta l'archivio immagini.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Inserimento di elementi dell'interfaccia utente nell'IDE  
 Il [menu](../../extensibility/menus-element.md) elemento [gruppi](../../extensibility/groups-element.md) elemento, e [pulsanti](../../extensibility/buttons-element.md) elemento contengono le definizioni per tutti i menu, gruppi e i comandi che sono definiti nel pacchetto. Inserire i menu, gruppi e i comandi nell'IDE usando un [padre](../../extensibility/parent-element.md) elemento che fa parte della definizione dell'elemento dell'interfaccia utente o mediante un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento che viene definito altrove.  
  
 Ogni `Menu`, `Group`, e `Button` elemento ha un `guid` attributo e un `id` attributo. Sempre impostato il `guid` attributo corrispondere al nome del `GuidSymbol` elemento che rappresenta il comando di impostare e il `id` il nome dell'attributo il `IDSymbol` elemento che rappresenta il menu, gruppo o comando per il `Symbols`sezione.  
  
##### <a name="to-define-ui-elements"></a>Per definire gli elementi dell'interfaccia utente  
  
1.  Se la definizione di qualsiasi nuovo menu, sottomenu, il menu di scelta rapida o le barre degli strumenti, aggiungere un `Menus` elemento per il `Commands` elemento. Quindi, per ciascuna voce di menu da creare, aggiungere un [Menu](../../extensibility/menu-element.md) elemento per il `Menus` elemento.  
  
     Impostare il `guid` e `id` gli attributi del `Menu` elemento e quindi impostare il `type` attributo al tipo di menu desiderato. È inoltre possibile impostare il `priority` attributo per stabilire la posizione relativa del menu del gruppo padre.  
  
    > [!NOTE]
    >  Il `priority` attributo non è valida per le barre degli strumenti e menu di scelta rapida.  
  
2.  Tutti i comandi nell'IDE di Visual Studio devono essere ospitati da gruppi di comandi che sono figli diretti del menu e barre degli strumenti. Se si aggiunge nuovi menu e barre degli strumenti all'IDE, queste devono contenere nuovi gruppi di comando. È anche possibile aggiungere gruppi di comandi di menu e barre degli strumenti esistenti in modo che è possibile raggruppare visivamente i comandi.  
  
     Quando si aggiungono nuovi gruppi di comando, è innanzitutto necessario creare un `Groups` elemento e quindi aggiungervi un [gruppo](../../extensibility/group-element.md) elemento per ogni gruppo di comando.  
  
     Impostare il `guid` e `id` gli attributi di ogni `Group` elemento e quindi impostare il `priority` attributo per stabilire la posizione relativa del gruppo nel menu del padre. Per ulteriori informazioni, vedere [creazione riutilizzabile gruppi di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Se si aggiungono nuovi comandi all'IDE, aggiungere un `Buttons` elemento per il `Commands` elemento. Quindi, per ogni comando, aggiungere un [pulsante](../../extensibility/button-element.md) elemento per il `Buttons` elemento.  
  
    1.  Impostare il `guid` e `id` gli attributi di ogni `Button` elemento e quindi impostare il `type` attributo al tipo di pulsante desiderato. È inoltre possibile impostare il `priority` attributo per stabilire la posizione relativa del comando nel gruppo padre.  
  
        > [!NOTE]
        >  Utilizzare `type="button"` per i comandi di menu standard e i pulsanti sulle barre degli strumenti.  
  
    2.  Nel `Button` elemento, aggiungere un [stringhe](../../extensibility/strings-element.md) elemento che contiene un [ButtonText](../../extensibility/buttontext-element.md) elemento e un [CommandName](../../extensibility/commandname-element.md) elemento. Il `ButtonText` elemento fornisce l'etichetta di testo per una voce di menu o la descrizione comando per un pulsante della barra degli strumenti. Il `CommandName` elemento fornisce il nome del comando da utilizzare nel comando.  
  
    3.  Se il comando sarà presente un'icona, creare un [icona](../../extensibility/icon-element.md) elemento il `Button` elemento e set relativo `guid` e `id` gli attributi di `Bitmap` elemento per l'icona.  
  
        > [!NOTE]
        >  Pulsanti della barra degli strumenti devono avere le icone.  
  
     Per ulteriori informazioni, vedere [tra oggetti MenuCommand e. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4.  Se i comandi richiedono le icone, aggiungere un [bitmap](../../extensibility/bitmaps-element.md) elemento per il `Commands` elemento. Quindi, per ogni icona, aggiungere un [Bitmap](../../extensibility/bitmap-element.md) elemento per il `Bitmaps` elemento. Questo è possibile specificare il percorso della risorsa bitmap. Per ulteriori informazioni, vedere [aggiunta di icone ai comandi di Menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
 È possibile basarsi sulla struttura elemento padre di posizionare correttamente la maggior parte dei menu, i gruppi e i comandi. Per il set di comandi di dimensioni molto grandi, o quando un menu, gruppo o comando deve apparire in più posizioni, si consiglia di specificare la selezione di comando.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Si affidano a elemento padre per inserire elementi dell'interfaccia utente nell'IDE  
  
1.  Per l'elemento padre tipico, creare un `Parent` ogni elemento `Menu`, `Group`, e `Command` elementi definiti nel pacchetto.  
  
     La destinazione di `Parent` elemento è il menu o gruppo che conterrà il menu, gruppo o comando.  
  
    1.  Impostare il `guid` il nome dell'attributo di `GuidSymbol` elemento che definisce il set di comandi. Se l'elemento di destinazione non fa parte del pacchetto, utilizzare il guid per il set di comandi, come definito nel file vsct corrispondente.  
  
    2.  Impostare il `id` attributo in modo che corrisponda il `id` attributo del menu di destinazione o del gruppo. Per un elenco di menu e i gruppi che sono esposte da Visual Studio, vedere [GUID e ID di Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e ID di Visual Studio le barre degli strumenti](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Se si dispone di un numero elevato di elementi dell'interfaccia utente da inserire nell'IDE, o se sono presenti elementi che devono essere visualizzate in più posizioni, definire le posizioni nel [CommandPlacements](../../extensibility/commandplacements-element.md) elemento, come illustrato nei passaggi seguenti.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Per usare il posizionamento di comando per inserire elementi dell'interfaccia utente nell'IDE  
  
1.  Dopo il `Commands` elemento, aggiungere un `CommandPlacements` elemento.  
  
2.  Nel `CommandPlacements` elemento, aggiungere un `CommandPlacement` elemento per ogni menu, un gruppo o un comando da inserire.  
  
     Ogni `CommandPlacement` elemento o `Parent` elemento inserisce un menu, gruppo o comando in un'unica posizione di IDE. Un elemento dell'interfaccia utente può avere un solo padre, ma può avere più elementi commandplacement. Per inserire un elemento dell'interfaccia utente in più posizioni, aggiungere un `CommandPlacement` elemento per ogni posizione.  
  
3.  Impostare il `guid` e `id` gli attributi di ogni `CommandPlacement` elemento al menu di hosting o gruppo, come farebbe un `Parent` elemento. È inoltre possibile impostare il `priority` attributo per stabilire la posizione relativa di elemento dell'interfaccia utente.  
  
 È possibile combinare posizionamento dall'elemento padre e il posizionamento di comando. Tuttavia, per il set di comandi di dimensioni molto grandi, si consiglia di utilizzare solo la selezione di comando.  
  
### <a name="adding-specialized-behaviors"></a>Aggiunta di comportamenti speciali  
 È possibile utilizzare [CommandFlag](../../extensibility/command-flag-element.md) elementi per modificare il comportamento di menu e comandi, ad esempio, per modificare l'aspetto e la visibilità. È inoltre possibile modificare quando un comando è visibile utilizzando [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), o aggiungere tasti di scelta rapida utilizzando [KeyBindings](../../extensibility/keybindings-element.md). Alcuni tipi di menu e comandi già dispone di un particolare comportamenti incorporati.  
  
##### <a name="to-add-specialized-behaviors"></a>Per aggiungere comportamenti speciali  
  
1.  Per rendere visibili solo in determinati contesti dell'interfaccia utente, ad esempio, un elemento dell'interfaccia utente quando viene caricata una soluzione, utilizzare i vincoli di visibilità.  
  
    1.  Dopo il `Commands` elemento, aggiungere un `VisibilityConstraints` elemento.  
  
    2.  Per ogni elemento dell'interfaccia utente limitare, aggiungere un [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.  
  
    3.  Per ogni `VisibilityItem` elemento, impostare il `guid` e `id` attributi per i menu, gruppo o comando e quindi impostare il `context` attributo nel contesto dell'interfaccia utente desiderato, come definito nel <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classe. Per ulteriori informazioni, vedere [VisibilityItem elemento](../../extensibility/visibilityitem-element.md).  
  
2.  Per impostare la visibilità o la disponibilità di un elemento dell'interfaccia utente nel codice, utilizzare uno o più dei flag di comando seguenti:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Per ulteriori informazioni, vedere [comando Flag elemento](../../extensibility/command-flag-element.md).  
  
3.  Per modificare come viene visualizzato un elemento o modificarne l'aspetto in modo dinamico, utilizzare uno o più dei flag di comando seguenti:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   PICT  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TestoConsente di modificare  
  
    -   TextOnly  
  
     Per ulteriori informazioni, vedere [comando Flag elemento](../../extensibility/command-flag-element.md).  
  
4.  Per modificare un elemento reazioni quando riceve i comandi, utilizzare uno o più dei flag di comando seguenti:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   Filtro tasti  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Per ulteriori informazioni, vedere [comando Flag elemento](../../extensibility/command-flag-element.md).  
  
5.  Per connettere una dipendenti dal menu di scelta rapida a un menu o un elemento in un menu, aggiungere un carattere e commerciale ('& ') nei `ButtonText` elemento per il menu o una voce di menu. Il carattere che segue la e commerciale è attivo tasto di scelta rapida quando viene aperto il menu padre.  
  
6.  Per associare una tasto indipendente dal menu di scelta rapida a un comando, utilizzare [KeyBindings](../../extensibility/keybindings-element.md). Per ulteriori informazioni, vedere [tasto di scelta rapida elemento](../../extensibility/keybinding-element.md).  
  
7.  Per localizzare il testo del menu, utilizzare il `LocCanonicalName` elemento. Per ulteriori informazioni, vedere [elemento stringhe](../../extensibility/strings-element.md).  
  
 Alcuni tipi di menu e pulsante includono particolari funzionalità. Nella tabella seguente vengono descritti alcuni menu specializzato e tipi di pulsanti. Per altri tipi, vedere il `types` attributo descrizioni in [elemento Menu](../../extensibility/menu-element.md), [elemento Button](../../extensibility/button-element.md), e [elemento combinata](../../extensibility/combo-element.md).  
  
 Casella combinata  
 Una casella combinata è un elenco di riepilogo a discesa che può essere utilizzato in una barra degli strumenti. Per aggiungere le caselle combinate all'interfaccia utente, creare un [casella combinata](../../extensibility/combos-element.md) elemento il `Commands` elemento. Aggiungere quindi il `Combos` elemento un `Combo` elemento per ogni casella combinata aggiungere. `Combo` gli elementi hanno gli stessi attributi e gli elementi figlio come `Button` elementi e hanno inoltre `DefaultWidth` e `idCommandList` attributi. Il `DefaultWidth` attributo imposta la larghezza in pixel e `idCommandList` attributo punti a un ID di comando che viene utilizzato per popolare la casella combinata. Per ulteriori informazioni, vedere il `Combo` la documentazione dell'elemento.  
  
 MenuController  
 Un controller di menu è un pulsante con una freccia accanto. Fare clic sulla freccia apre un elenco. Per aggiungere un controller di menu per l'interfaccia utente, creare un `Menu` elemento e impostare il relativo `type` attributo **MenuController** o **MenuControllerLatched**, in base al comportamento desiderato. Per popolare un controller di menu, impostarlo come elemento padre di un `Group` elemento. Il controller di menu visualizzerà tutti gli elementi figlio di tale gruppo nel relativo elenco a discesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)