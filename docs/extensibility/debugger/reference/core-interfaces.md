---
title: Interfacce di base | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45521c0db16ac892d2e0e43e34c4b030075f7be2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="core-interfaces"></a>Interfacce di base
Le interfacce seguenti sono le interfacce di base per l'estensione del debugger utilizzando il [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Discussione  
 Queste interfacce vengono utilizzate principalmente per creare il motore di debug (DE). Essi sono organizzate in categorie:  
  
-   [Punti di interruzione](#Breakpoints)  
  
-   [Contesti](#Contexts)  
  
-   [In modalità Server Core](#CoreServer)  
  
-   [Motori di debug](#DebugEngines)  
  
-   [Documenti](#Documents)  
  
-   [Eventi](#Events)  
  
-   [Espressioni](#Expressions)  
  
-   [Memoria](#Memory)  
  
-   [Moduli](#Modules)  
  
-   [Porte](#Ports)  
  
-   [Processi](#Processes)  
  
-   [Programmi](#Programs)  
  
-   [Proprietà](#Properties)  
  
-   [Stack frame](#StackFrames)  
  
-   [Thread](#Threads)  
  
-   [Visualizzatori di tipo](#TypeVisualizers)  
  
 Le entità che possono implementare le interfacce sono:  
  
-   Eseguire il debug del motore (Germania)  
  
-   Fornitore della porta (PS)  
  
-   Analizzatore di espressioni (Java EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> Punti di interruzione  
 Queste interfacce sono correlate per l'implementazione e il rilevamento di punti di interruzione.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Rappresenta un punto di interruzione associato a una posizione di memoria.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Quando un punto di interruzione è associata a una posizione di memoria, inviati tramite la Germania.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Rappresenta un checksum di documento per una richiesta di punto di interruzione.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Quando un punto di interruzione non riesce a essere associato a una posizione di memoria, inviati tramite la Germania.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Inviato per la Germania quando viene raggiunto un punto di interruzione.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Rappresenta una richiesta per un punto di interruzione; utilizzata per creare un punto di interruzione in sospeso.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Rappresenta una richiesta per un punto di interruzione; utilizzata per creare un punto di interruzione in sospeso.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Rappresenta le informazioni utilizzate per associare un punto di interruzione.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Inviato per la Germania quando non è associato un punto di interruzione da una posizione di memoria.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Rappresenta un punto di interruzione non valido (restituito da `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Rappresenta le informazioni di risoluzione su un punto di interruzione non valido.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Rappresenta una posizione in una funzione in cui è stato impostato un punto di interruzione.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Rappresenta un punto di interruzione che deve essere associato. utilizzata per creare un punto di interruzione associato.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione associati.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione che non è stato possibile associare a una posizione di memoria.|  
  
##  <a name="Contexts"></a> Contesti  
 Queste interfacce rappresentano vari tipi di contesti all'interno del programma sottoposto a debug.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Rappresenta la posizione iniziale di un'istruzione di codice.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Estende il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia per abilitare il recupero delle interfacce di modulo e processo.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VISUAL STUDIO, GERMANIA|Rappresenta una posizione in un documento.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Rappresenta il contesto in cui valutare un'espressione.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Rappresenta la posizione iniziale nella memoria di una raccolta di byte.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto di stack frame in un punto di interruzione o un'eccezione.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta un contesto di stack frame in un punto di interruzione o un'eccezione.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Rappresenta un'enumerazione su un set dei contesti di codice.|  
  
##  <a name="CoreServer"></a> In modalità Server Core  
 Queste interfacce rappresentano il computer in cui un programma viene eseguito il debug. Questi vengono implementati da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ma può essere chiamato dai motori di debug.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fornisce accesso alle porte e fornitori di porte, nonché informazioni relative al computer.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Rappresenta un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) che supporta il debug remoto.|  
  
##  <a name="DebugEngines"></a> Motori di debug  
 Queste interfacce rappresentano i motori di debug e i relativi eventi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Rappresenta un motore di debug personalizzati.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Rappresenta un motore di debug personalizzato che supporta il caricamento di simboli, JustMyCode ed eccezioni.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Inviato da ogni nuova istanza della DE per indicare che è possibile gestire le attività di debug.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Rappresenta un motore di debug personalizzato che supporta l'esecuzione dei programmi.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|GERMANIA, PS|Rappresenta un nodo di programma che gestisce più motori di debug.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Fornisce un modo per SDM ottenere un'interfaccia per il motore di debug di un thread, un programma o un frame dello stack.|  
  
##  <a name="Documents"></a> Documenti  
 Queste interfacce rappresentano documenti (file di origine) e i relativi elementi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Inviato per la Germania per richiedere un documento da aprire.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Rappresenta un flusso di istruzioni disassemblate da un documento.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VISUAL STUDIO, GERMANIA|Rappresenta un documento fornito per la Germania, specificando un nome e un ID di classe (CLSID).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|GERMANIA, EE|Rappresenta un checksum per un documento di debug e consente di passare il valore di checksum tra i componenti.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VISUAL STUDIO, GERMANIA|Rappresenta un contesto di documento, una posizione all'interno di un documento corrispondente a un particolare contesto di istruzione e il codice.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VISUAL STUDIO, GERMANIA|Rappresenta una posizione generale all'interno di un documento.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Rappresenta una posizione in un file di origine come un offset di carattere.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VISUAL STUDIO, GERMANIA|Rappresenta un documento di testo fornito per la Germania (derivato da [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), fornire il testo effettivo.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Per specificare le modifiche in un file di origine in memoria, inviati tramite la Germania.|  
  
##  <a name="Events"></a> Eventi  
 Queste interfacce rappresentano tutti gli eventi che vengono inviati tra la Germania e gestore di sessione di debug (SDM).  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Inviato per la Germania per richiedere un documento da aprire.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Il motore di debug (DE) invia questa interfaccia per la gestione di debug (SDM) per impostare lo stato di sessione barra messaggio durante il caricamento di simboli.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Inviato per la Germania quando è stata completata un'interruzione del programma.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Inviato dalla Germania quando è associato un punto di interruzione.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Inviato dalla Germania quando un punto di interruzione si verifica un errore da associare.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Inviato per la Germania quando viene raggiunto un punto di interruzione.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Inviato per la Germania quando non è associato un punto di interruzione.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Inviato per la Germania per determinare se deve essere arrestata in una determinata posizione.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Per specificare le modifiche in un file di origine in memoria, inviati tramite la Germania.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Inviato da ogni nuova istanza della DE per indicare che è possibile gestire le attività di debug.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Inviato per la Germania per indicare il programma in fase di debug è pronto per l'esecuzione della prima istruzione.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Interfaccia che viene utilizzata da altre interfacce di evento, che potrebbero restituire un errore, per fornire messaggi di errore leggibile.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|GERMANIA, PS|Interfaccia di base da cui tutti gli altri eventi interfacce sono derivate.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Rappresenta un'interfaccia implementata dal suo SDM a cui vengono inviati gli eventi (espressi sotto forma di oggetti che implementano un'interfaccia di evento specifico).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Quando si verifica un'eccezione nel programma sottoposto a debug, inviati tramite la Germania.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Inviato dalla Germania quando è stata completata una valutazione di un'espressione asincroni.|  
|IDebugFindSymbolEvent2||OBSOLETE. NON USARE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Inviato per la Germania quando è stata completata l'elaborazione di un'eccezione intercettata.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Inviato dalla Germania quando un programma ha terminato il caricamento.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Inviato da DE per avere la visualizzazione dell'IDE di un messaggio informativo all'utente.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Inviato dalla Germania quando un modulo viene caricato o scaricato.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Segnala il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per avvertire l'utente che non sono possibile trovare l'eseguibile avviato simboli del debugger.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Inviato da DE per avere la visualizzazione IDE una stringa arbitraria.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VISUAL STUDIO, GERMANIA|Inviato da una porta per comunicare gli eventi porta per ogni listener.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando è stato creato un processo.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando un processo è stato eliminato.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando è stato creato un programma.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando un programma è stato eliminato.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Consente di eseguire l'override del comportamento predefinito di un motore di debug di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente quando si termina una sessione di debug.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Inviato dal motore di debug (DE) al gestore di sessione di debug (SDM) quando viene modificato il nome di un programma.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Inviato da DE quando una nuova proprietà (rappresentato dal `IDebugProperty2` interface) è stato creato.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Inviato dalla Germania quando una proprietà è stata eliminata.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Inviato per la Germania quando si passa da o in una funzione, pertanto il valore restituito può essere visualizzato correttamente.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Abilita motori per leggere le impostazioni metriche di debug in modalità remota.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Inviato per la Germania quando un passaggio in, failover o un'istruzione è stato completato.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Inviato per la Germania per indicare l'esito positivo o negativo del caricamento dei simboli per un modulo.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Inviato dalla Germania quando un thread è stato creato.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Inviato dalla Germania quando un thread è stato eliminato.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Inviato dalla Germania quando un thread è stato modificato il relativo nome.|  
  
##  <a name="Expressions"></a> Espressioni  
 Queste interfacce rappresentano le espressioni da valutare in un particolare contesto.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Rappresenta un'espressione da valutare. Ottenuta il [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Rappresenta un contesto in cui viene valutata un'espressione. Ottenuta il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Inviato dalla Germania quando è stata completata una valutazione di un'espressione asincroni.|  
  
##  <a name="Memory"></a> Memoria  
 Queste interfacce rappresentano le sequenze di byte in memoria.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Rappresenta una sequenza di byte in memoria che è possibile leggere o scrivere.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Rappresenta una posizione in memoria di una sequenza di byte.|  
  
##  <a name="Modules"></a> Moduli  
 Queste interfacce rappresentano un modulo, che corrisponde a un file eseguibile o. File DLL.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Rappresenta un singolo file eseguibile o DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Rappresenta un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che supporta i simboli.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Inviato dalla Germania quando un modulo viene caricato o scaricato.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Rappresenta le informazioni sul server di origine che è contenuti in un file PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Rappresenta un'enumerazione su un set di moduli che sono noti a un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> Porte  
 Queste interfacce rappresentano le porte e i fornitori di porte.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VISUAL STUDIO, PS|Rappresenta la porta predefinita nel computer locale.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Consente a un motore di debug che utilizza DCOM per richiedere il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per assicurarsi che il firewall non blocca il debug remoto.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VISUAL STUDIO, PS|Rappresenta una porta.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Inviato da una porta per comunicare gli eventi porta per ogni listener.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Rappresenta una porta che può avviare e terminare i processi.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Usato per registrare e annullare la registrazione programmi con una porta. consente alla porta tenere traccia in corso il debug di programmi.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Rappresenta un'interfaccia utente personalizzata per la selezione della porta.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Rappresenta una richiesta per una porta da cui non verrà creata una nuova porta o si trova.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Rappresenta un fornitore di porte.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Rappresenta un fornitore di porte che può rendere persistente (Salva su disco) le informazioni sulle porte è creato.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Consente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per visualizzare il testo all'interno di **informazioni sul trasporto** sezione del **Connetti a processo** la finestra di dialogo.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Consente di eseguire query per informazioni relative al computer di destinazione.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VISUAL STUDIO, PS|Rappresenta un'enumerazione su un set di porte.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Rappresenta un'enumerazione su un set di fornitori di porte.|  
  
##  <a name="Processes"></a> Processi  
 Queste interfacce rappresentano processi, un singolo file eseguibile contenente uno o più programmi.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, GERMANIA|Rappresenta un processo in esecuzione in un computer.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, GERMANIA|Rappresenta un processo in modo attivo supporta debug (utilizzato per sostituire passaggio, continuare ed eseguire metodi sul [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando è stato creato un processo.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando un processo è stato eliminato.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Rappresenta un processo che è necessario tenere traccia di sessione di cui è associato.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Rappresenta un'enumerazione di un set di processi su una porta.|  
  
##  <a name="Programs"></a> Programmi  
 Queste interfacce rappresentano i programmi, unità logiche di esecuzione che non corrispondono necessariamente a un modulo o un eseguibile fisico.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Rappresenta un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che è necessario collaborare con altri programmi in corso il debug contemporaneamente.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|GERMANIA, PS|Rappresenta un'unità logica di esecuzione.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando è stato creato un programma.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|GERMANIA, PS|Inviato da DE o alla porta quando un programma è stato eliminato.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|GERMANIA, PS|Rappresenta un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che può essere gestito da più motori di debug.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Rappresenta un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che deve essere in grado di tenere traccia di sessione di cui è associato.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|GERMANIA, PS|Rappresenta un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che può restituire informazioni sul processo in cui è in esecuzione.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|GERMANIA, PS|Rappresenta un programma che è possibile eseguire il debug.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|GERMANIA, PS|Consente a un nodo di programma ricevere una notifica di un tentativo di connettersi al programma associato.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Fornisce un modo per SDM eseguire una query un DE sui programmi controllati da tale DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Usato da DEs per registrare i programmi con SDM per mostrare che sono in fase di debug.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|GERMANIA, PS|Rappresenta un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che può effettuare il marshalling di interfacce attraverso i limiti di thread o processo.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|GERMANIA, PS|Rappresenta un'enumerazione di un set di applicazioni.|  
  
##  <a name="Properties"></a> Proprietà  
 Queste interfacce rappresentano le proprietà, un valore associato a un contesto specifico, in genere il risultato della valutazione di un'espressione.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Rappresenta un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che può visualizzare il relativo valore in modo personalizzato.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Rappresenta un valore di uno stack frame, documento o il risultato della valutazione di un'espressione.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Rappresenta un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che supporta le stringhe di lunghe arbitraria.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Inviato da DE quando una nuova proprietà (rappresentato dal [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface) è stato creato.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Inviato dalla Germania quando una proprietà è stata eliminata.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Rappresenta un riferimento a una proprietà che può esistere all'esterno di un determinato stack frame.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Rappresenta un'enumerazione su un set di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture che descrivono variabili, registri, parametri ed espressioni.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Rappresenta un'enumerazione su un set di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture.|  
  
##  <a name="StackFrames"></a> Stack frame  
 Queste interfacce rappresentano uno stack frame, un contesto in cui un punto di interruzione o un'eccezione è stata eseguita.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto in cui un punto di interruzione o un'eccezione è stata eseguita.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che può gestire intercettate eccezioni.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Rappresenta un'enumerazione sul set di [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) strutture che specificano la funzione chiamata sequenza utilizzata per giungere a un determinato stack frame.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Rappresenta un'enumerazione su un set di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture, che descrivono gli stack frame.|  
  
##  <a name="Threads"></a> Thread  
 Queste interfacce rappresentano thread e i relativi eventi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Rappresenta un thread di esecuzione.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Inviato dalla Germania quando un thread è stato creato.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Inviato dalla Germania quando un thread è stato eliminato.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Inviato dalla Germania quando un thread è stato modificato il relativo nome.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Rappresenta un'enumerazione su un set di thread.|  
  
##  <a name="TypeVisualizers"></a> Visualizzatori di tipo  
 Queste interfacce forniscono il supporto per i visualizzatori di tipo. Queste interfacce vengono in genere implementate tramite un analizzatore di espressioni.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Rappresenta una matrice di byte da inviare a un visualizzatore di tipo.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fornisce metodi per ottenere l'accesso ai dati da passare a un visualizzatore di tipo.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Rappresenta una proprietà che fornisce l'accesso a [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Creazione di un motore di debug personalizzato](../../../extensibility/debugger/creating-a-custom-debug-engine.md)