---
title: Tipi di eventi supportati | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6b308aabacf5a82f4ea630ccae256c56526f793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supported-event-types"></a>Tipi di eventi supportati
Il debug di Visual Studio supporta attualmente i tipi di evento seguente:  
  
-   Eventi asincroni  
  
     Inviare una notifica di gestore di sessione di debug (SDM) e l'IDE lo stato dell'applicazione in corso il debug in fase di modifica. Questi eventi vengono elaborati le libero del SDM e l'IDE. Nessuna risposta viene inviata al motore di debug (DE) dopo l'elaborazione dell'evento. Il [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfacce sono esempi di eventi asincroni.  
  
-   Eventi sincroni  
  
     Notificare il SDM e l'IDE lo stato dell'applicazione in corso il debug in fase di modifica. L'unica differenza tra gli eventi e gli eventi asincroni è che viene inviata una risposta tramite il [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metodo.  
  
     L'invio di un evento sincrono è utile se è necessario il DE per continuare l'elaborazione dopo che l'IDE riceve ed elabora l'evento.  
  
-   Sincrono eventi di arresto o eventi di arresto  
  
     Notificare il SDM e l'IDE che l'applicazione in corso il debug è stato arrestato l'esecuzione del codice. Quando si invia un evento di arresto tramite il metodo [evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametro è obbligatorio. Gli eventi di arresto derivati da una chiamata a uno dei metodi seguenti:  
  
    -   [Eseguire](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di eventi di arresto.  
  
    > [!NOTE]
    >  Non sono supportati gli eventi di interruzione asincrona. È un errore per inviare un evento di interruzione asincrona.  
  
## <a name="discussion"></a>Discussione  
 L'implementazione effettiva degli eventi varia a seconda della progettazione della Germania. Il tipo di ogni evento inviato è determinato dai relativi attributi, che vengono impostate quando si progetta la Germania. Ad esempio, inviare uno Germania un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) come un evento asincrono, mentre un altro può inviare i dati come un evento di arresto.  
  
 Nella tabella seguente specifica i parametri del programma e i thread sono necessari per quali eventi, nonché i tipi di evento. Qualsiasi evento possa essere sincrono. Nessun evento deve essere sincrone.  
  
> [!NOTE]
>  Il [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfaccia è obbligatoria per tutti gli eventi.  
  
|event|IDebugProgram2|IDebugThread2|Eventi di arresto|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non è consentito|Non è consentito|No|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non è consentito|Non è consentito|No|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|Può essere|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|Può essere|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|Può essere|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
|IDebugStopCompleteEvent2|Obbligatorio|Obbligatorio|Yes|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|È consentito, ma non obbligatorio|È consentito, ma non obbligatorio|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Invio di eventi](../../extensibility/debugger/sending-events.md)