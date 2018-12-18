---
title: Metodi correlati al punto di interruzione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5bf80b78545242a625b9c3e212c101712ecbd9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoint-related-methods"></a>Metodi correlati al punto di interruzione
Un motore di debug (DE) deve supportare l'impostazione di punti di interruzione. Il debug di Visual Studio supporta i seguenti tipi di punti di interruzione:  
  
-   Associato  
  
     Richiesta tramite l'interfaccia utente e associato correttamente in un percorso di codice specificato  
  
-   In sospeso  
  
     Richiesto tramite l'interfaccia utente ma non è ancora associato a effettivo istruzioni  
  
## <a name="discussion"></a>Discussione  
 Ad esempio, un punto di interruzione in sospeso si verifica quando le istruzioni non sono stati ancora caricate. Quando viene caricato il codice, in sospeso provare i punti di interruzione da associare al codice in corrispondenza della posizione prescritta, vale a dire, per inserire istruzioni di interruzione nel codice. Gli eventi vengono inviati al gestore di sessione di debug (SDM) per indicare l'associazione ha esito positivo o per notificare che si sono verificati errori di associazione.  
  
 Un punto di interruzione in sospeso gestisce inoltre l'elenco interno dei punti di interruzione associati corrispondente. Un punto di interruzione può causare l'inserimento di molti punti di interruzione nel codice. Debug dell'interfaccia utente di Visual Studio Mostra una visualizzazione albero delle interruzioni in sospeso e i relativi punti di interruzione associati.  
  
 Creare e utilizzare in sospeso i punti di interruzione è necessaria l'implementazione del [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) (metodo), nonché i metodi seguenti della [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfacce.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se un oggetto punto di interruzione è possibile associare a un percorso di codice.|  
|[Operazione di binding](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa un oggetto specificato in sospeso punto di interruzione per uno o più percorsi di codice.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione in sospeso.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta di punto di interruzione utilizzata per creare un punto di interruzione in sospeso.|  
|[Abilitare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva o disattiva lo stato di abilitazione di un punto di interruzione in sospeso.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da un punto di interruzione in sospeso.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore derivanti da un punto di interruzione in sospeso.|  
|[Eliminazione](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto di interruzione in sospeso e tutti i punti di interruzione associati da esso.|  
  
 Per enumerare i punti di interruzione associati e i punti di interruzione di errore, è necessario implementare tutti i metodi di [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e di [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 In attesa di punti di interruzione da associare a un codice di percorso richiede l'implementazione delle operazioni seguenti [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) metodi.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione associato.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione di punto di interruzione che descrive un punto di interruzione.|  
|[Abilitare](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Abilita o disabilita un punto di interruzione.|  
|[Eliminazione](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto di interruzione associato.|  
  
 Risoluzione e richiedere informazioni richiedono l'implementazione del seguente [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) metodi.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da una risoluzione.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione di punto di interruzione che descrive un punto di interruzione.|  
  
 Risoluzione degli errori che potrebbero verificarsi durante l'associazione richiede l'implementazione delle seguenti [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) metodi.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione di errore.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori di punto di interruzione che descrive un punto di interruzione di errore.|  
  
 Risoluzione degli errori che potrebbero verificarsi durante l'associazione richiede inoltre i metodi seguenti della [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo di un punto di interruzione.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni di risoluzione di un punto di interruzione.|  
  
 Visualizzazione del codice sorgente in un punto di interruzione è necessario implementare i metodi di [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e/o i metodi di [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)