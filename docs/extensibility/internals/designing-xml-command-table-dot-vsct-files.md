---
title: Progettazione tabella comandi XML (. File Vsct) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e007ffe8cf3cc893bc9575a3e7c083090b523467
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="designing-xml-command-table-vsct-files"></a>Progettazione tabella comandi XML (. File Vsct)
Un file di tabella (vsct) del comando XML descrive il layout e l'aspetto degli elementi di comando per un pacchetto VSPackage. Gli elementi di comando includono pulsanti, caselle combinate, menu, barre degli strumenti e gruppi di elementi di comando. Questo argomento descrive XML file tabella di comando, loro influenza menu e voci di comando e come crearli.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>I comandi, menu, gruppi e i File con estensione vsct  
 i file con estensione vsct organizzati in gruppi di comandi, menu e comandi. Tag XML nel file vsct rappresentano ognuno di questi elementi, insieme ad altri elementi associati, ad esempio i pulsanti di comando, la selezione di comando e bitmap.  
  
 Quando si crea un nuovo VSPackage eseguendo il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modello di pacchetto, il modello genera un file con estensione vsct con gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato, a seconda delle selezioni. Questo file con estensione vsct può quindi essere modificato per soddisfare i requisiti di un VSPackage specifico. Per esempi su come modificare un file vsct, vedere gli esempi in [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Per creare un file con estensione vsct vuoto, vedere [procedura: creare una. Il File Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una volta creata, aggiungere elementi, attributi e valori XML al file per descrivere il layout dell'elemento di comando. Per uno schema XML dettagliato, vedere il [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Differenze tra file CTC e con estensione vsct  
 Mentre il significato di tag XML in un file con estensione vsct sarà uguali a quelli ora deprecata il formato di file CTC, la relativa implementazione è leggermente diversa.  
  
-   Il nuovo  **\<extern >** tag è in cui si fa riferimento altri file con estensione h da compilare, ad esempio quelle per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra degli strumenti.  
  
-   Mentre il supporto di file con estensione vsct il **/ includono** istruzione, come file CTC, anche una nuova funzionalità \< **importare >** elemento. È la differenza, **/ includono** riporta **tutti** delle informazioni, ma \< **importare >** consente solo i nomi.  
  
-   Mentre i file CTC richiedono un file di intestazione in cui è possibile definire le direttive del preprocessore, uno non è richiesto per i file con estensione vsct. Al contrario, inserire le direttive nella tabella dei simboli, si trova nel  **\<simbolo >** elementi, nella parte inferiore del file con estensione vsct.  
  
-   funzionalità dei file con estensione vsct un  **\<annotazione >** tag, che consente di incorporare le informazioni desiderate, ad esempio note o persino le immagini.  
  
-   I valori vengono archiviati come attributi dell'elemento.  
  
-   Flag di comando può essere archiviato singolarmente o in pila.  IntelliSense, tuttavia, non funziona sui flag di comando in pila. Per ulteriori informazioni sui flag di comando, vedere il [comando Flag elemento](../../extensibility/command-flag-element.md).  
  
-   È possibile specificare più tipi, ad esempio divisione elenchi a discesa, casella combinata e così via.  
  
-   GUID non vengono convalidati.  
  
-   Ogni elemento dell'interfaccia utente è una stringa che rappresenta il testo che viene visualizzato con esso.  
  
-   Elemento padre è facoltativo. Se omesso, viene utilizzato il valore "Gruppo sconosciuto".  
  
-   L'icona di argomento è facoltativo.  
  
-   La sezione bitmap, lo stesso come un CTC file, ad eccezione del fatto che è ora possibile specificare un nome di file tramite href che vengono spostate dal compilatore vsct.exe in fase di compilazione.  
  
-   ResID - l'ID di risorsa bitmap precedente può essere utilizzato e ancora funziona allo stesso modo come file CTC.  
  
-   HRef - un nuovo metodo che consente di specificare un nome di file per la risorsa della bitmap. Si presuppone che tutte siano utilizzate, pertanto è possibile omettere la sezione utilizzata. Il compilatore eseguirà la ricerca per le risorse locali per il file, quindi scegliere le condivisioni di rete e le risorse definite per l'opzione /I prima.  
  
-   Tasto di scelta rapida, Non è necessario specificare un emulatore. Se si specifica uno, il compilatore presupporrà che l'editor e l'emulatore sono uguali.  
  
-   Keychord - è stato eliminato. Il nuovo formato è Key1, Mod1, Key2, Mod2.  È possibile specificare un carattere, esadecimale o costante VK.  
  
 Il nuovo compilatore vsct.exe, compila i file CTC sia con estensione vsct. Il compilatore ctc.exe precedente, tuttavia, verrà riconosce né compila i file con estensione vsct.  
  
 È possibile utilizzare il compilatore vsct.exe per convertire un file CTO esistente in un file con estensione vsct. Per ulteriori informazioni, vedere [procedura: creare una. File Vsct da un oggetto esistente. File CTO](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
## <a name="the-vsct-file-elements"></a>Elementi del File con estensione vsct  
 La tabella di comando include la gerarchia e gli elementi seguenti:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) : rappresenta tutti i comandi, i gruppi di menu e menu associati al pacchetto VSPackage.  
  
 [Elemento extern](../../extensibility/extern-element.md) : fa riferimento a tutti i file esterni. h che si desidera unire con il file con estensione vsct.  
  
 [L'elemento di inclusione](../../extensibility/include-element.md) : fa riferimento a qualsiasi file di intestazione aggiuntivi (h) che si desidera compilare con il file your.vsct. Un file con estensione vsct può includere file h che contiene le costanti che definiscono i comandi, gruppi di menu e menu che fornisce l'IDE o un altro VSPackage.  
  
 [I comandi elemento](../../extensibility/commands-element.md) : rappresenta tutti i singoli comandi che possono essere eseguiti. Ogni comando presenta i seguenti quattro elementi figlio:  
  
 [Elemento menu](../../extensibility/menus-element.md) : rappresenta tutti i menu e barre degli strumenti in VSPackage. I menu sono contenitori per i gruppi di comandi.  
  
 [Groups-elemento](../../extensibility/groups-element.md) : rappresenta tutti i gruppi nel pacchetto VSPackage. I gruppi sono raccolte di singoli comandi.  
  
 [I pulsanti elemento](../../extensibility/buttons-element.md) : rappresenta tutti i pulsanti di comando e le voci di menu nel pacchetto VSPackage. I pulsanti sono controlli visivi che possono essere associati a comandi.  
  
 [Elemento bitmap](../../extensibility/bitmaps-element.md) -rappresenta tutte le bitmap per tutti i pulsanti nel pacchetto VSPackage. Bitmap sono immagini che vengono visualizzate accanto a o sui pulsanti di comando, a seconda del contesto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) : indica altre posizioni in cui i singoli comandi devono essere posizionati nel menu di un VSPackage.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) : Specifica se un comando consente di visualizzare affatto volte o solo in determinati contesti, ad esempio quando viene visualizzata una finestra di dialogo specifico o una finestra. Menu e comandi che hanno un valore per questo elemento verranno visualizzato solo quando è attivo il contesto specificato. Il comportamento predefinito consiste nel visualizzare il comando in qualsiasi momento.  
  
 [Tasti di scelta rapida elemento](../../extensibility/keybindings-element.md) : specifica qualsiasi tasti di scelta rapida per i comandi. Vale a dire, una o più combinazioni di tasti che è necessario tenere premute per eseguire il comando, ad esempio **CTRL + S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) : Informs il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente anche se il comando specificato è implementato da altro codice, quando il pacchetto VSPackage corrente è attivo, fornisce l'implementazione del comando.  
  
 `Symbols Element`: Contiene i nomi dei simboli e gli ID di GUID per tutti i comandi nel pacchetto.  
  
## <a name="vsct-file-design-guidelines"></a>. Linee guida di progettazione il File Vsct  
 Per progettare correttamente un file vsct, seguire queste linee guida.  
  
-   Comandi possono essere inseriti solo nei gruppi, gruppi possono essere inseriti solo nei menu e menu possono essere inseriti solo nei gruppi. Solo i menu sono effettivamente visualizzati nell'IDE, gruppi e i comandi non lo sono.  
  
-   Sottomenu non possono essere assegnati direttamente a un menu, ma devono essere assegnati a un gruppo, che a sua volta viene assegnato a un menu.  
  
-   Per un gruppo padre o menu tramite il campo padre della loro definizione direttiva è possono assegnare i comandi, sottomenu e gruppi.  
  
-   Organizzazione di una tabella di comando esclusivamente tramite i campi padre nelle direttive ha una limitazione importante. Le direttive che definiscono gli oggetti possono richiedere l'argomento di un solo padre.  
  
-   Riutilizzo di comandi, gruppi o i sottomenu richiede l'utilizzo di una direttiva di nuovo per creare una nuova istanza dell'oggetto con il proprio `GUID:ID` coppia.  
  
-   Ogni `GUID:ID` coppia deve essere univoca. Riutilizzo di un comando, ad esempio, situato in un menu, una barra degli strumenti o un menu di scelta rapida, viene gestito dal <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.  
  
-   Comandi sia sottomenu possono anche essere assegnati a più gruppi e gruppi possono essere assegnati a più menu usando il [elemento Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Il File Vsct note  
 Se si apportano modifiche a un file con estensione vsct dopo aver sia, compilarlo e inserirlo in una DLL satellite nativa, è consigliabile eseguire **devenv.exe /setup /nosetupvstemplates**. In questo modo forza specificate nel Registro di sistema sperimentale per essere rileggere e il database interno che descrive le risorse di VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da ricompilare.  
  
 Durante lo sviluppo, è possibile per più progetti di VSPackage essere creato e registrato nell'hive del Registro di sistema sperimentale che può causare confusione confusione nell'IDE. Per risolvere questo problema, è possibile reimpostare l'hive sperimentale per le impostazioni predefinite per rimuovere registrati tutti i pacchetti VSPackage e le modifiche apportate all'IDE. Per ripristinare l'hive sperimentale, utilizzare lo strumento CreateExpInstance.exe fornito con Visual Studio SDK. È possibile trovare in  
  
 **% PROGRAMFILES (x86) %\Visual Studio \<versione > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Eseguire lo strumento da riga di comando **CreateExpInstance /Reset**. Tenere presente che questo strumento consente di rimuovere dall'hive sperimentale i package VS registrati che normalmente non vengono installati con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../../extensibility/extending-menus-and-commands.md)