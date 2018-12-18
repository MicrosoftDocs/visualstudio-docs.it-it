---
title: BP_REQUEST_INFO2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11402c5ad188b72600debb5cb64b7f2811e75ee9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bprequestinfo2"></a>BP_REQUEST_INFO2
Contiene le informazioni necessarie per implementare un punto di interruzione, tra cui fornitore GUID, vincoli e punto di analisi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_REQUEST_INFO2 {  
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
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```csharp  
public struct BP_REQUEST_INFO2 {  
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
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
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
  
 `guidVendor`  
 GUID del fornitore. Può essere un valore null.  
  
 `bstrConstraint`  
 Nome del vincolo di punto di interruzione. Può essere un valore null.  
  
 `bstrTracepoint`  
 Nome del punto di traccia. Può essere un valore null.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita dal [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)