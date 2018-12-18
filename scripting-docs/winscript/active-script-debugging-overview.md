---
title: Panoramica del debug di script ActiveX | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9aebdc3f8fa4df0f4386609e632e1a8611c87f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-debugging-overview"></a>Panoramica del debug di script ActiveX
Le interfacce di debug di script ActiveX consentono un debug indipendente dal linguaggio e dall'host e supportano un'ampia gamma di ambienti di sviluppo.  
  
 ![Processo host script](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Figura 1  
  
 Un ambiente di debug indipendente dal linguaggio può supportare qualsiasi linguaggio di programmazione o combinazione di linguaggi, senza informazioni specifiche per questi linguaggi. L'ambiente di debug supporta anche l'esecuzione e i punti di interruzione per linguaggi diversi. Questa panoramica è incentrata principalmente sui linguaggi di scripting per il supporto, ad esempio VBScript e [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Un debugger indipendente dall'host può essere usato automaticamente con qualsiasi host di scripting, ad esempio Internet Explorer o un host personalizzato. L'host controlla gli elementi che il debugger presenta all'utente, dalla struttura ad albero dei documenti al contenuto e alla colorazione basata sulla sintassi dei documenti di debug. In questo modo il codice sorgente già sottoposto a debug può essere visualizzato nel contesto del documento host. Ad esempio in Internet Explorer è possibile visualizzare uno script in una pagina HTML.  
  
 Nelle sottosezioni riportate di seguito vengono descritti i singoli componenti chiave del debug ActiveX e le interfacce associate. Prima di procedere è tuttavia necessario definire alcuni concetti chiave del debug ActiveX:  
  
 applicazione host  
 Applicazione che ospita i motori script e offre un set di oggetti per la generazione di script (o "modello a oggetti").  
  
 modulo di gestione del linguaggio  
 Componente che offre astrazioni di analisi, esecuzione e debug per un determinato linguaggio.  
  
 ambiente di sviluppo integrato (IDE) debugger  
 Applicazione che rende disponibile l'interfaccia utente di debug comunicando con l'applicazione host e i moduli del linguaggio.  
  
 gestione del debug del computer  
 Componente che gestisce un registro dei processi dell'applicazione dei quali è possibile eseguire il debug.  
  
 gestione del debug dei processi  
 Componente che gestisce l'albero dei documenti di cui è possibile eseguire il debug per una particolare applicazione, tiene traccia dei thread in esecuzione e così via.  
  
 contesto del documento  
 Un contesto del documento è un'astrazione che rappresenta un intervallo specifico del codice sorgente di un documento host.  
  
 contesto del codice  
 Un contesto del codice rappresenta una determinata posizione nel codice in esecuzione di un modulo di gestione del linguaggio (un "puntatore di istruzione virtuale").  
  
 contesto dell'espressione  
 Contesto specifico (ad esempio uno stack frame) nel quale le espressioni possono essere valutate da un modulo di gestione del linguaggio.  
  
 esplorazione di oggetti  
 Rappresentazione strutturata indipendente dal linguaggio del nome, tipo, valore e degli oggetti secondari di un oggetto, adatta per implementare un'interfaccia utente di tipo "finestra espressioni di controllo".  
  
 Di seguito viene inclusa una panoramica dei componenti principali del debug Active X e delle interfacce associate corrispondenti, seguita dai dettagli relativi a tali interfacce.  
  
## <a name="language-engine"></a>Modulo di gestione del linguaggio  
 Il modulo di gestione del linguaggio offre:  
  
-   Analisi ed esecuzione del linguaggio.  
  
-   Supporto per il debug (punti di interruzione e così via).  
  
-   Valutazione delle espressioni.  
  
-   Colorazione della sintassi.  
  
-   Esplorazione di oggetti.  
  
-   Enumerazione e analisi dello stack.  
  
 Di seguito sono elencate le interfacce che un motore di script deve supportare per offrire debug, valutazione delle espressioni ed esplorazione di oggetti. Queste interfacce vengono usate dall'applicazione host per il mapping tra il contesto di documento e i contesti di codice del motore. Vengono anche usate dall'interfaccia utente del debugger per la valutazione delle espressioni, l'enumerazione dello stack e l'esplorazione di oggetti.  
  
 [Interfaccia IActiveScriptDebug](../winscript/reference/iactivescriptdebug-interface.md)  
 Specifica l'enumerazione di contesto del codice e la colorazione della sintassi.  
  
 [Interfaccia IActiveScriptErrorDebug](../winscript/reference/iactivescripterrordebug-interface.md)  
 Restituisce i contesti del documento e gli stack frame per gli errori.  
  
 [Interfaccia IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md)  
 Collegamento specificato dall'host tra il motore di script e il debugger.  
  
 [Interfaccia IDebugCodeContext](../winscript/reference/idebugcodecontext-interface.md)  
 Specifica un "puntatore dell'istruzione" virtuale in un thread.  
  
 [Interfaccia IEnumDebugCodeContexts](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 Enumera i contesti di codice che corrispondono a un contesto di documento.  
  
 [Interfaccia IDebugStackFrame](../winscript/reference/idebugstackframe-interface.md)  
 Rappresenta uno stack frame logico nello stack di thread.  
  
 [Interfaccia IDebugExpressionContext](../winscript/reference/idebugexpressioncontext-interface.md)  
 Specifica un contesto per la valutazione delle espressioni.  
  
 [Interfaccia IDebugStackFrameSniffer](../winscript/reference/idebugstackframesniffer-interface.md)  
 Consente di enumerare gli stack frame logici.  
  
 [Interfaccia IDebugExpression](../winscript/reference/idebugexpression-interface.md)  
 Rappresenta un'espressione valutata in modo asincrono.  
  
 [Interfaccia IDebugSyncOperation](../winscript/reference/idebugsyncoperation-interface.md)  
 Consente a un motore di script l'astrazione di un'operazione che deve essere eseguita mentre è annidata in un thread bloccato specifico.  
  
 [Interfaccia IDebugAsyncOperation](../winscript/reference/idebugasyncoperation-interface.md)  
 Specifica l'accesso asincrono a un'operazione di debug sincrono.  
  
 [Interfaccia IDebugAsyncOperationCallBack](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 Specifica gli eventi di stato associati allo stato di una valutazione di interfaccia `IDebugAsyncOperation`.  
  
 [Interfaccia IEnumDebugExpressionContexts](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 Enumera una raccolta di oggetti `IDebugExpressionContexts`.  
  
 [Interfaccia IProvideExpressionContexts](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 Consente di enumerare i contesti di espressione noti a un determinato componente.  
  
 [Interfaccia IDebugFormatter](../winscript/reference/idebugformatter-interface.md)  
 Consente a un linguaggio o un IDE di personalizzare la conversione tra valori VARIANT o tipi VARTYPE e stringhe.  
  
 [Interfaccia IDebugStackFrameSnifferEx](../winscript/reference/idebugstackframesnifferex-interface.md)  
 Enumera gli stack frame logici per PDM.  
  
## <a name="hosts"></a>Host  
 L'host:  
  
-   Ospita i moduli di gestione del linguaggio.  
  
-   Specifica un modello a oggetti (insieme di oggetti inseribili nello script).  
  
-   Definisce un albero di documenti dei quali è possibile eseguire il debug e il contenuto dei documenti.  
  
-   Organizza gli script in applicazioni virtuali.  
  
 Esistono due tipi di host:  
  
-   Un dumb host supporta solo l'esecuzione delle interfacce di scripting di base. Non è presente alcun controllo sulla struttura o sull'organizzazione dei documenti, che sono determinate interamente dagli script resi disponibili ai moduli di linguaggio.  
  
-   Uno smart host supporta un set di interfacce più grande, che consente di definire la struttura di documenti, il contenuto del documento e la colorazione della sintassi. Un set di interfacce helper descritte nella sottosezione successiva semplifica notevolmente l'esecuzione di un host come smart host.  
  
### <a name="smart-host-helper-interfaces"></a>Interfacce helper Smart Host  
 I metodi `IDebugDocumentHelper` offrono un set di interfacce notevolmente semplificate che un host può usare per ottenere i vantaggi dell'hosting smart senza dover gestire la complessità (e la portata) delle interfacce host complete.  
  
 Ovviamente l'uso delle interfacce da parte dell'host non è obbligatorio. Tuttavia usando queste interfacce è possibile evitare l'implementazione o l'uso di molte interfacce più complesse.  
  
 [Interfaccia IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implementata da PDM, offre implementazioni per molte interfacce necessarie per l'hosting smart.  
  
 [Interfaccia IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md)  
 Implementata (facoltativamente) dall'host per esporre al debugger funzionalità specifiche dell'host, ad esempio la colorazione della sintassi.  
  
 Per altre informazioni, vedere [Implementazione delle interfacce helper Smart Host](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Interfacce Smart Host complete  
 Di seguito viene elencato il set completo di interfacce che uno smart host deve implementare o usare se non usa le interfacce helper.  
  
 Interfacce implementate dall'host:  
  
 [Interfaccia IDebugDocumentInfo](../winscript/reference/idebugdocumentinfo-interface.md)  
 Specifica informazioni su un documento del quale è stata creata o meno un'istanza.  
  
 [Interfaccia IDebugDocumentProvider](../winscript/reference/idebugdocumentprovider-interface.md)  
 Specifica i mezzi per creare un'istanza di un documento su richiesta.  
  
 [Interfaccia IDebugDocument](../winscript/reference/idebugdocument-interface.md)  
 Interfaccia di base per tutti i documenti di debug.  
  
 [Interfaccia IDebugDocumentText](../winscript/reference/idebugdocumenttext-interface.md)  
 Specifica l'accesso a una versione di solo testo del documento di debug.  
  
 [Interfaccia IDebugDocumentTextAuthor](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Consente la modifica della versione di solo testo del documento di debug.  
  
 [Interfaccia IDebugDocumentContext](../winscript/reference/idebugdocumentcontext-interface.md)  
 Offre una rappresentazione astratta di una parte del documento sottoposto a debug.  
  
 Interfacce implementate da PDM per conto dell'host:  
  
 [Interfaccia IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Estende la funzionalità dell'interfaccia `IDebugDocumentProvider` offrendo un contesto in un albero di progetto.  
  
## <a name="debugger-ide"></a>IDE debugger  
 IDE è un'interfaccia utente di debug indipendente dal linguaggio. Fornisce:  
  
-   Visualizzatori/editor di documenti.  
  
-   Gestione dei punti di interruzione.  
  
-   Finestre di controllo e valutazione delle espressioni.  
  
-   Esplorazione dello stack frame.  
  
-   Esplorazione oggetto/classe.  
  
-   Esplorazione della struttura dell'applicazione virtuale.  
  
 Interfacce implementate dal debugger:  
  
 [Interfaccia IApplicationDebugger](../winscript/reference/iapplicationdebugger-interface.md)  
 Interfaccia primaria esposta da una sessione IDE debugger.  
  
 [Interfaccia IApplicationDebuggerUI](../winscript/reference/iapplicationdebuggerui-interface.md)  
 Offre a un componente esterno maggior controllo sull'interfaccia utente (UI) del debugger.  
  
 [Interfaccia IDebugExpressionCallBack](../winscript/reference/idebugexpressioncallback-interface.md)  
 Specifica eventi di stato per lo stato della valutazione `IDebugExpression`.  
  
 [Interfaccia IDebugDocumentTextEvents](../winscript/reference/idebugdocumenttextevents-interface.md)  
 Specifica eventi che indicano le modifiche per il documento di testo associato.  
  
 [Interfaccia IDebugApplicationNodeEvents](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 Specifica l'interfaccia evento per l'interfaccia `IDebugApplicationNode`.  
  
### <a name="machine-debug-manager"></a>Gestione debug del computer  
 La gestione debug del computer rappresenta il punto di contatto tra le applicazioni virtuali e i debugger, mediante la gestione e l'enumerazione di un elenco di applicazioni virtuali attive.  
  
 [Interfaccia IDebugSessionProvider](../winscript/reference/idebugsessionprovider-interface.md)  
 Definisce una sessione di debug per un'applicazione in esecuzione.  
  
 [Interfaccia IMachineDebugManager](../winscript/reference/imachinedebugmanager-interface.md)  
 Interfaccia principale della gestione debug del computer.  
  
 [Interfaccia IMachineDebugManagerCookie](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Questa interfaccia, simile all'interfaccia `IMachineDebugManager`, supporta i cookie di debug.  
  
 [Interfaccia IMachineDebugManagerEvents](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Segnala le modifiche all'elenco di applicazioni in esecuzione gestite dalla gestione del debug del computer.  
  
 [Interfaccia IEnumRemoteDebugApplications](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Enumera le applicazioni in esecuzione in un computer.  
  
### <a name="process-debug-manager"></a>Gestione del debug dei processi  
 La gestione debug dei processi esegue le operazioni seguenti:  
  
-   Sincronizza il debug di più moduli di gestione del linguaggio.  
  
-   Gestisce una struttura ad albero di documenti di cui è possibile eseguire il debug.  
  
-   Unisce gli stack frame.  
  
-   Coordina i punti di interruzione e le sequenze di passaggi tra i diversi moduli di gestione del linguaggio.  
  
-   Tiene traccia dei thread.  
  
-   Gestisce un thread debugger per l'elaborazione asincrona.  
  
-   Comunica con la gestione debug del computer e l'IDE di debug.  
  
 Di seguito sono elencate le interfacce specificate dalla gestione del debug dei processi.  
  
 [Interfaccia IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md)  
 Interfaccia principale con la gestione del debug dei processi. Questa interfaccia può creare, aggiungere o rimuovere un'applicazione virtuale da un processo.  
  
 [Interfaccia IRemoteDebugApplication](../winscript/reference/iremotedebugapplication-interface.md)  
 Rappresenta un'applicazione in esecuzione.  
  
 [Interfaccia IDebugApplication](../winscript/reference/idebugapplication-interface.md)  
 Espone i metodi di debug non usabili in remoto per l'uso con gli host e i moduli di gestione del linguaggio.  
  
 [Interfaccia IRemoteDebugApplicationThread](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 Rappresenta un thread di esecuzione all'interno di una determinata applicazione.  
  
 [Interfaccia IDebugApplicationThread](../winscript/reference/idebugapplicationthread-interface.md)  
 Consente ai moduli e agli host di gestione del linguaggio di offrire la sincronizzazione dei thread e di gestire le informazioni sullo stato di debug specifiche a livello di thread.  
  
 [Interfaccia IEnumRemoteDebugApplicationThreads](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 Enumera i thread in esecuzione in un'applicazione.  
  
 [Interfaccia IDebugThreadCall](../winscript/reference/idebugthreadcall-interface.md)  
 Invia le chiamate con marshalling.  
  
 [Interfaccia IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Gestisce una posizione per un documento nella gerarchia.  
  
 [Interfaccia IEnumDebugApplicationNodes](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 Enumera i nodi figlio di un nodo associato a un'applicazione.  
  
 [Interfaccia IEnumDebugStackFrames](../winscript/reference/ienumdebugstackframes-interface.md)  
 Enumera gli stack frame corrispondenti a un thread e uniti a partire dai motori.  
  
 [Interfaccia IDebugCookie](../winscript/reference/idebugcookie-interface.md)  
 Consente l'impostazione del cookie di debug nei debugger di script.  
  
 [Interfaccia IDebugHelper](../winscript/reference/idebughelper-interface.md)  
 Funziona come factory per visualizzatori oggetto e punti di connessione semplici per i motori di script.  
  
 [Interfaccia ISimpleConnectionPoint](../winscript/reference/isimpleconnectionpoint-interface.md)  
 Specifica una soluzione semplice per la descrizione e l'enumerazione agli eventi generati in un punto di connessione specifico per i motori di script.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del debugger di script ActiveX](../winscript/reference/active-script-debugger-interfaces.md)