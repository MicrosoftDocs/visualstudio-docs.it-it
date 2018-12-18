---
title: BP_REQUEST_INFO | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e317f360eaa796eb8bdbea2a58950c8b72a3fef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
Contiene le informazioni necessarie per implementare un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```csharp  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## <a name="members"></a>Membri  
 `dwFields`  
 Una combinazione di flag dal [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumerazione che specifica quali campi vengono compilati.  
  
 `guidLanguage`  
 GUID del linguaggio.  
  
 `bpLocation`  
 Il [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura che specifica il tipo del punto di interruzione.  
  
 `pProgram`  
 Il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta l'applicazione in cui si verifica il punto di interruzione.  
  
 `bstrProgramName`  
 Il nome dell'applicazione in cui si verifica il punto di interruzione.  
  
 `pThread`  
 Il [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread in cui si verifica il punto di interruzione.  
  
 `bstrThreadName`  
 Il nome del thread in cui si verifica il punto di interruzione.  
  
 `bpCondition`  
 Il [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struttura che descrive le condizioni in cui verrà generato il punto di interruzione.  
  
 `bpPassCount`  
 Il [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struttura che contiene le informazioni relative al conteggio di passaggio del punto di interruzione.  
  
 `dwFlags`  
 Una combinazione di flag dal [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumerazione che specifica i flag per il punto di interruzione richiesta.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita dal [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) metodo.  
  
 Se è necessario ottenere il fornitore del motore di debug GUID, il vincolo di punto di interruzione o il punto di analisi, vedere il [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)