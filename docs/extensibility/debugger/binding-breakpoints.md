---
title: Associazione dei punti di interruzione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efda5969e7022f8c44d7060a29ee31fbc5968d96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="binding-breakpoints"></a>Associazione dei punti di interruzione
Se l'utente imposta un punto di interruzione, ad esempio premendo F9, l'IDE in cui viene creata la richiesta e richiede la sessione di debug per creare il punto di interruzione.  
  
## <a name="setting-a-breakpoint"></a>Impostazione di un punto di interruzione  
 L'impostazione di un punto di interruzione è un processo in due passaggi, perché il codice o i dati interessati dal punto di interruzione potrebbero non essere ancora disponibili. Innanzitutto, il punto di interruzione deve essere descritte, e quindi come codice o i dati diventano disponibili, deve essere associato a tale codice o dati, come indicato di seguito:  
  
1.  Il punto di interruzione viene richiesto dai motori di debug pertinente (DEs), e quindi il punto di interruzione è associata al codice o dati appena sarà disponibile.  
  
2.  La richiesta di punto di interruzione viene inviata per la sessione di debug, che invia tutti DEs pertinente. Qualsiasi Germania che sceglie di gestire il punto di interruzione consente di creare un oggetto corrispondente in sospeso punto di interruzione.  
  
3.  La sessione di debug raccoglie i punti di interruzione in sospeso e li invia al pacchetto di debug (il componente di debug di Visual Studio).  
  
4.  Il pacchetto di debug richiede la sessione di debug per associare il punto di interruzione in sospeso a codice o i dati. La sessione di debug invia la richiesta a tutti DEs pertinente.  
  
5.  Se la Germania è in grado di associare il punto di interruzione, viene inviato che un punto di interruzione associato evento nuovamente alla sessione di debug. In caso contrario, invia un evento di errore del punto di interruzione.  
  
## <a name="pending-breakpoints"></a>Punti di interruzione in sospeso  
 Un punto di interruzione in sospeso è possibile associare a più percorsi di codice. Ad esempio, una riga di codice sorgente per un modello di C++ è possibile associare a ogni sequenza di codice generato dal modello. La sessione di debug è possibile utilizzare un evento associato del punto di interruzione per enumerare i contesti di codice associati a un punto di interruzione al momento che l'evento è stato inviato. Più contesti di codice possono essere associati in un secondo momento, in modo che la Germania può inviare che più punti di interruzione associato gli eventi per ogni richiesta di associazione. Tuttavia, un Germania deve inviare un solo evento di errore di punto di interruzione per ogni richiesta di associazione.  
  
## <a name="implementation"></a>Implementazione  
 A livello di codice, il pacchetto di debug chiama il debug di sessione di gestione (SDM) e le assegna un [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaccia che esegue il wrapping di un [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) struttura, che descrive il punto di interruzione. Anche se i punti di interruzione può essere di vario tipo, vengono risolte in un contesto di codice o i dati.  
  
 Il SDM passa la chiamata a ogni DE rilevanti chiamando il relativo [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metodo. Se la Germania sceglie di gestire il punto di interruzione, crea e restituisce un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia. Il SDM raccoglie queste interfacce e li passa al pacchetto di debug come singolo `IDebugPendingBreakpoint2` interfaccia.  
  
 Finora, gli eventi non sono stati generati.  
  
 Il pacchetto di debug tenta quindi di associare il punto di interruzione in sospeso al codice o dati chiamando [associare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), che viene implementato per la Germania.  
  
 Se è associato il punto di interruzione, la Germania invia un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaccia eventi per il pacchetto di debug. Il pacchetto debug viene utilizzata questa interfaccia consente di enumerare tutti i contesti di codice (o il contesto dei dati singolo) associata al punto di interruzione chiamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), che restituisce uno o più [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfacce. Il [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfaccia restituisce un [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaccia e [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) restituisce un [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) un'unione che contiene il codice o i dati di contesto.  
  
 Se la Germania è in grado di associare il punto di interruzione, viene inviato un singolo [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaccia eventi per il pacchetto di debug. Il pacchetto di debug recupera il tipo di errore (errore o avviso) e un messaggio informativo chiamando [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguito da [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Restituisce un [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura che contiene il tipo di errore e il messaggio.  
  
 Se un Germania gestisce un punto di interruzione, ma non è possibile eseguirne l'associazione, viene restituito un errore di tipo `BPET_TYPE_ERROR`. Il pacchetto di debug risponde visualizzando una finestra di dialogo di errore e l'IDE posiziona un'icona di punto esclamativo all'interno dell'icona di punto di interruzione a sinistra della riga di codice sorgente.  
  
 Se un Germania gestisce un punto di interruzione, non è possibile associare, ma un'altra Germania può eseguirne l'associazione, viene restituito un avviso. L'IDE risponde inserendo un glifo del punto all'interno dell'icona di punto di interruzione a sinistra della riga di codice sorgente.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)