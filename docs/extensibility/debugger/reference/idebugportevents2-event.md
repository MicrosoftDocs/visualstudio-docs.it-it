---
title: IDebugPortEvents2::Event | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9f1394e09cc6b7b695d1d19dee1f46df09f8514
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Questo metodo invia gli eventi che indicano la creazione e l'eliminazione dei processi e i programmi su una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pMachine`  
 [in] Un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) oggetto che rappresenta il server di debug (ne esista uno per ogni istanza di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) in cui si è verificato l'evento.  
  
 `pPort`  
 [in] Un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) oggetto che rappresenta la porta in cui si è verificato l'evento.  
  
 `pProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) oggetto che rappresenta il processo in cui si è verificato l'evento.  
  
 `pProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma in cui si è verificato l'evento.  
  
 `pEvent`  
 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) oggetto che identifica l'evento. Gli eventi possibili sono i seguenti:  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 [in] Il GUID dell'evento. Poiché l'evento viene eseguito il cast a [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) prima di chiamare questo metodo, questo identificatore rende più semplice determinare quali eventi vengono inviati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)