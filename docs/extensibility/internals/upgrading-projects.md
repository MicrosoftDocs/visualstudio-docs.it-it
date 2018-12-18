---
title: Aggiornamento di progetti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 060823a04127480ef8de387200425a34c6ef1178
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="upgrading-projects"></a>L'aggiornamento di progetti
Modifiche al modello di progetto da una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al successivo potrebbe essere necessario aggiornare progetti e soluzioni in modo che eseguano la versione più recente. Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornisce interfacce che possono essere utilizzate per implementare il supporto di aggiornamento nei propri progetti.  
  
## <a name="upgrade-strategies"></a>Strategie di aggiornamento  
 Per supportare un aggiornamento, l'implementazione di sistema di progetto è necessario definire e implementare una strategia di aggiornamento. Per determinare la strategia, è possibile scegliere per il supporto di backup side-by-side (SxS), il backup di copia o entrambi.  
  
-   Backup SxS significa che un progetto copia solo i file che è necessario eseguire l'aggiornamento sul posto, aggiunta di un suffisso di nome file appropriato, ad esempio, "old".  
  
-   Backup di copia indica che un progetto copia tutti gli elementi di progetto in un percorso di backup fornito dall'utente. I relativi file nel percorso di progetto originale vengono quindi aggiornati.  
  
## <a name="how-upgrade-works"></a>Come funziona l'aggiornamento  
 Quando una soluzione creata in una versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene aperto in una versione più recente, i controlli IDE file della soluzione per determinare se deve essere aggiornato. Se l'aggiornamento è obbligatorio, il **aggiornamento guidato** viene avviata automaticamente per l'utente attraverso il processo di aggiornamento guidato.  
  
 Quando una soluzione deve eseguire l'aggiornamento, viene eseguita una query ogni factory del progetto per la propria strategia di aggiornamento. La strategia determina se la factory del progetto supporta il backup di copia o SxS. Le informazioni vengono inviate per il **aggiornamento guidato**, che raccoglie le informazioni necessarie per il backup e presenta le opzioni applicabili all'utente.  
  
### <a name="multi-project-solutions"></a>Soluzioni multiprogetto  
 Se una soluzione contiene più progetti e le strategie di aggiornamento sono diversi, ad esempio quando un progetto C++ che supporta solo backup SxS e un progetto Web che supportano solo backup di copia, le factory del progetto devono negoziare della strategia di aggiornamento.  
  
 Ogni factory del progetto per una query nella soluzione <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Chiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> per verificare se i file di progetto globale è necessario eseguire l'aggiornamento e per determinare le strategie di aggiornamento supportate. Il **aggiornamento guidato** viene quindi richiamata.  
  
 Dopo che l'utente completa la procedura guidata, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> viene chiamato su ogni factory del progetto per eseguire l'aggiornamento effettivo. Per semplificare i backup, IVsProjectUpgradeViaFactory metodi forniscono il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servizio per registrare i dettagli del processo di aggiornamento. Questo servizio non può essere memorizzato nella cache.  
  
 Dopo aver aggiornato tutti i file rilevanti globali, ogni factory del progetto è possibile scegliere di creare un'istanza di un progetto. L'implementazione del progetto deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> viene quindi chiamato il metodo per aggiornare tutti gli elementi di progetto rilevanti.  
  
> [!NOTE]
>  Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo non fornisce il servizio SVsUpgradeLogger. Questo servizio può essere ottenuto chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Suggerimenti  
 Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio per verificare se è possibile modificare un file prima di modificarlo e possibile salvarlo prima di salvarlo. Ciò consentirà il backup e aggiornamento implementazioni gestiscono i file di progetto nel controllo del codice sorgente, i file con autorizzazioni insufficienti e così via.  
  
 Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante tutte le fasi di backup del servizio e l'aggiornamento per fornire informazioni sull'esito positivo o negativo del processo di aggiornamento.  
  
 Per ulteriori informazioni sul backup e l'aggiornamento di progetti, vedere i commenti per IVsProjectUpgrade in vsshell2.idl.  
  
## <a name="upgrading-custom-projects"></a>Aggiornamento di progetti personalizzati
Se si modificano le informazioni rese persistenti nel file di progetto tra diverse versioni di Visual Studio del prodotto, è necessario supportare l'aggiornamento del file di progetto dalla versione precedente a quella nuova. Per supportare l'aggiornamento che consente di partecipare di **conversione guidata di Visual Studio**, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia. Questa interfaccia contiene l'unico meccanismo disponibile per l'aggiornamento della copia. L'aggiornamento del progetto viene eseguito all'apertura di una parte della soluzione. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia è implementata dalla factory del progetto, o almeno deve essere ottenuta dalla factory del progetto.  
  
 Il meccanismo precedente che utilizza il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia è ancora supportata, ma concettualmente aggiorna il sistema di progetto come parte del progetto aperto. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia viene pertanto chiamata dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente anche se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia è chiamata o implementata. Questo approccio consente di utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> per implementare la copia solo le parti dell'aggiornamento del progetto e delegare il resto del lavoro da eseguire sul posto (possibilmente nella nuova posizione), il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia.  
  
 Per un esempio di implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, vedere [esempi di VSSDK](http://aka.ms/vs2015sdksamples).  
  
 Con gli aggiornamenti di progetti si verificano i seguenti scenari:  
  
-   Se il file è di un formato più recente rispetto a quelli supportati dal progetto, deve restituire un errore che segnala il problema. Si presuppone che la versione precedente del prodotto include codice per verificare la versione.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flag specificato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (metodo), l'aggiornamento verrà implementato come un aggiornamento sul posto prima dell'apertura del progetto.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flag specificato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo, l'aggiornamento viene implementato come un aggiornamento della copia.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag specificato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiamare, quindi l'utente è stato richiesto dall'ambiente di aggiornare il file di progetto come un aggiornamento sul posto, dopo il progetto è aperto. Ad esempio, l'ambiente richiede all'utente di eseguire l'aggiornamento all'apertura di una versione precedente della soluzione.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag non è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiamare, è necessario richiedere all'utente di aggiornare il file di progetto.  
  
     Di seguito è riportato un esempio di messaggio di richiesta dell'aggiornamento:  
  
     "Il progetto '%1' è stato creato con una versione precedente di Visual Studio. Se si apre il progetto con la versione in uso, potrebbe risultare impossibile aprirlo con le versioni precedenti di Visual Studio. Continuare e aprire il progetto?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Per implementare IVsProjectUpgradeViaFactory  
  
1.  Implementare il metodo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia, in particolare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> nell'implementazione di factory del progetto, metodo o rendere le implementazioni richiamabili dall'implementazione della factory del progetto.  
  
2.  Se si desidera eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> come il `VSPUVF_FLAGS` parametro il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementazione.  
  
3.  Se si desidera eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> come il `VSPUVF_FLAGS` parametro il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementazione.  
  
4.  Per entrambi i passaggi 2 e 3, operazioni utilizzando per l'aggiornamento del file effettivo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, può essere implementato come descritto nel "implementazione `IVsProjectUpgade`" sezione riportata di seguito, oppure è possibile delegare l'aggiornamento del file effettivo a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Utilizzare i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> alla fase successiva all'aggiornamento correlata messaggi per l'utente utilizzando la migrazione guidata di Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>interfaccia viene utilizzata per implementare qualsiasi tipo di aggiornamento dei file che deve essere eseguito come parte dell'aggiornamento del progetto. Questa interfaccia non viene chiamata da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ma viene fornito come un meccanismo per aggiornare i file che fanno parte del sistema del progetto, ma il sistema di progetto principale potrebbe non essere direttamente a conoscenza. Questa situazione può ad esempio verificarsi se i file e le proprietà relativi al compilatore non vengono gestiti dallo stesso team di sviluppo che gestisce il resto del sistema del progetto.  
  
### <a name="ivsprojectupgrade-implementation"></a>Implementazione di IVsProjectUpgrade  
 Se il sistema di progetto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , possa non partecipare solo il **conversione guidata di Visual Studio**. Tuttavia, anche se si implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia, è comunque possibile delegare l'aggiornamento di file a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementazione.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Per implementare IVsProjectUpgrade  
  
1.  Quando un utente tenta di aprire un progetto, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metodo viene chiamato dall'ambiente dopo che il progetto viene aperto e prima di qualsiasi altro utente azione possa essere eseguita sul progetto. Se l'utente era già stato richiesto di aggiornare la soluzione, quindi il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag viene passato il `grfUpgradeFlags` parametro. Se l'utente apre direttamente un progetto, tale esempio usando il **Aggiungi progetto esistente** comando, il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag non è stato passato e il progetto deve richiedere all'utente di eseguire l'aggiornamento.  
  
2.  In risposta al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiamata, il progetto deve valutare se il file di progetto viene aggiornato. Se il progetto non è necessario aggiornare il tipo di progetto a una nuova versione, quindi può semplicemente restituire il <xref:Microsoft.VisualStudio.VSConstants.S_OK> flag.  
  
3.  Se il progetto deve aggiornare il tipo di progetto a una nuova versione, quindi deve determinare se il file di progetto può essere modificato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo e passando un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il `rgfQueryEdit` parametro. Il progetto deve quindi eseguire le operazioni seguenti:  
  
    -   Se il `VSQueryEditResult` valore restituito nel `pfEditCanceled` parametro <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, quindi l'aggiornamento può continuare perché il file di progetto può essere scritto.  
  
    -   Se il `VSQueryEditResult` valore restituito nel `pfEditCanceled` parametro <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e `VSQueryEditResult` valore ha il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit impostato, quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deve restituire un errore, perché gli utenti devono risolvere il problema di autorizzazioni autonomamente. Il progetto deve quindi eseguire le operazioni seguenti:  
  
         Segnalare l'errore all'utente chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> e restituire il <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> codice di errore <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Se il `VSQueryEditResult` valore <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e `VSQueryEditResultFlags` valore ha la <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit impostato, quindi il file di progetto deve essere estratto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> chiamata sul file di progetto determina il file per l'estrazione e la versione più recente da recuperare, quindi il progetto viene scaricato e ricaricato. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metodo viene chiamato nuovamente dopo la creazione di un'altra istanza del progetto. In questa seconda chiamata, il file di progetto può essere scritto sul disco. È consigliabile che il progetto salvi una copia del file di progetto nel formato precedente con un'estensione OLD, apporti le modifiche necessarie per l'aggiornamento e salvi il file di progetto nel nuovo formato. Anche se qualsiasi parte del processo di aggiornamento non riesce, il metodo deve indicare l'errore restituendo <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Questo determina lo scaricamento del progetto da Esplora soluzioni.  
  
     È importante comprendere l'intero processo che si verifica nell'ambiente per il caso in cui la chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo (specificando un valore di ReportOnly) restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> flag.  
  
5.  L'utente tenta di aprire il file di progetto.  
  
6.  L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementazione.  
  
7.  Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> restituisce `true`, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementazione.  
  
8.  L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementazione per aprire il file e inizializzare l'oggetto di progetto, ad esempio Progetto1.  
  
9. L'ambiente chiama l'implementazione di `IVsProjectUpgrade::UpgradeProject` per determinare se il file di progetto deve essere aggiornato.  
  
10. Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passare un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il `rgfQueryEdit` parametro.  
  
11. L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> per `VSQueryEditResult` e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit viene impostato `VSQueryEditResultFlags`.  
  
12. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementazione chiama `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Questa chiamata può causare l'estrazione di una nuova copia del file di progetto e il recupero della versione più recente, nonché rendere necessario ricaricare il file di progetto. A questo punto, può verificarsi una delle due situazioni seguenti:  
  
-   Se si gestisce autonomamente il ricaricamento progetto, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementazione (VSITEMID_ROOT). Quando si riceve questa chiamata, ricaricare la prima istanza del progetto (Project1) e continuare l'aggiornamento del file di progetto. L'ambiente sa che si gestisce il propria ricaricamento del progetto se si restituisce `true` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Se non si gestisce autonomamente il ricaricamento progetto, quindi tornare `false` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). In questo caso, prima di <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) restituisce, l'ambiente crea un'altra nuova istanza del progetto, ad esempio Project2, come indicato di seguito:  
  
    1.  L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sul primo oggetto di progetto, Project1, quindi posizionare questo oggetto nello stato inattivo.  
  
    2.  L'ambiente chiama l'implementazione di `IVsProjectFactory::CreateProject` per creare una seconda istanza del progetto, Project2.  
  
    3.  L'ambiente chiama l'implementazione di `IPersistFileFormat::Load` per aprire il file e inizializzare il secondo oggetto di progetto, Project2.  
  
    4.  L'ambiente chiama `IVsProjectUpgrade::UpgradeProject` una seconda volta per determinare se l'oggetto di progetto deve essere aggiornato. Tuttavia, questa chiamata viene eseguita su una nuova, seconda, istanza del progetto, Project2. Si tratta del progetto aperto nella soluzione.  
  
        > [!NOTE]
        >  Nell'istanza di cui il primo progetto, Project1, si trova nello stato inattivo, quindi è necessario restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> dalla prima chiamata ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementazione.  
  
    5.  Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passare un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il `rgfQueryEdit` parametro.  
  
    6.  L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e l'aggiornamento può continuare perché il file di progetto può essere scritto.  
  
 Se non è possibile eseguire l'aggiornamento, restituire <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> da `IVsProjectUpgrade::UpgradeProject`. Se non è necessario eseguire l'aggiornamento o si sceglie di non eseguirlo, gestire la chiamata `IVsProjectUpgrade::UpgradeProject` come un'operazione che non produce effetti. Se si restituisce <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, viene aggiunto un nodo segnaposto alla soluzione per il progetto.  
  
## <a name="upgrading-project-items"></a>Aggiornamento degli elementi di progetto
  
Se si aggiunge o gestire gli elementi all'interno dei sistemi di progetto non viene implementato, devi partecipano al processo di aggiornamento del progetto. Crystal Reports è riportato un esempio di un elemento che può essere aggiunto al sistema del progetto.  
  
 Gli implementatori di elemento di progetto in genere consigliabile utilizzare un progetto già completamente un'istanza e aggiornato perché è necessario conoscere quali il tipo di progetto sono riferimenti e le altre proprietà del progetto sono presenti per prendere una decisione di aggiornamento.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Per ricevere le notifiche di aggiornamento del progetto  
  
1.  Impostare il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flag (definito in vsshell80.idl) nell'implementazione dell'elemento di progetto. In questo modo l'elemento di progetto VSPackage automaticamente quando caricare le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell determina che un sistema di progetto è in corso l'aggiornamento.  
  
2.  Consigliare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia tramite la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metodo.  
  
3.  Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia viene generata dopo il completamento delle operazioni di aggiornamento dell'implementazione del sistema di progetto e viene creato il nuovo progetto aggiornato. A seconda dello scenario, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia generata dopo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodi.  
  
### <a name="to-upgrade-the-project-item-files"></a>Per aggiornare i file di elemento di progetto  
  
1.  Nell'implementazione dell'elemento di progetto, è necessario gestire attentamente il processo di backup di file. Ciò vale in particolare per un backup, side-by-side in cui il `fUpgradeFlag` parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> è impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, in cui vengono collocati i file che erano stato eseguito il backup lungo file lato designati come "old". File di backup precedenti all'ora di sistema quando è stato aggiornato il progetto possono essere definiti come non aggiornata. Inoltre, potrebbe essere sovrascritto a meno che non eseguire passi specifici per evitare questo problema.  
  
2.  Al momento l'elemento di progetto Ottiene una notifica di aggiornamento del progetto, il **conversione guidata di Visual Studio** viene ancora visualizzato. Pertanto, è necessario utilizzare i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaccia per fornire messaggi di aggiornamento per l'interfaccia utente della procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [Progetti](../../extensibility/internals/projects.md)   
