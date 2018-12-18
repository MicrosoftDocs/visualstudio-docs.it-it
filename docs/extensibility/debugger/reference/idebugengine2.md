---
title: IDebugEngine2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2
helpviewer_keywords: IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 95a1a8c48bd6eab0f21ccc85a125b5d10f42ef4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2"></a>IDebugEngine2
Questa interfaccia rappresenta un motore di debug (DE). Consente di gestire diversi aspetti di una sessione di debug, dalla creazione di punti di interruzione per l'impostazione e la cancellazione di eccezioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia è implementata da un DE personalizzato per gestire il debug dei programmi. Questa interfaccia deve essere implementata per la Germania.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) per gestire la sessione di debug, incluse la gestione delle eccezioni, la creazione di punti di interruzione e rispondere agli eventi sincroni inviati per la Germania.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugEngine2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumeratore per tutti i programmi in corso il debug da un DE.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Associa un DE a un programma.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto di interruzione in sospeso la Germania.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Specifica come la Germania deve gestire una determinata eccezione.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Rimuove l'eccezione specificata in modo che non viene gestita dal motore di debug.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Rimuove l'elenco delle eccezioni, che l'IDE è impostato per un linguaggio o una particolare architettura di runtime.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ottiene il GUID della DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa un Germania che il programma specificato è stato insolitamente terminato e che la Germania necessario pulire tutti i riferimenti al programma e invio di un programma evento di eliminazione.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chiamato da SDM per indicare che un evento di debug sincrona, per la Germania precedentemente inviato SDM, è stato ricevuto ed elaborato.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Imposta le impostazioni locali della DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Imposta la radice del Registro di sistema attualmente in uso per la Germania.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Imposta una metrica.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Richiede che tutti i programmi in corso il debug da questo DE arrestare l'esecuzione alla successiva esecuzione di uno dei relativi thread tenta di eseguire.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Che modo GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)