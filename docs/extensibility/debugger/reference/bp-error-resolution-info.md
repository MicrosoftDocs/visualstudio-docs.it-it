---
title: BP_ERROR_RESOLUTION_INFO | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9fdf3b6aee272990fb22feee13f8e46ee8550073
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
Descrive la risoluzione di un punto di interruzione di errore, ad esempio percorso, software e thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>Membri  
 `dwFields`  
 Una combinazione dei valori di [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) enumerazione che specifica quali campi della struttura sono stati compilati.  
  
 `bpResLocation`  
 Il [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) unione, che specifica il percorso di risoluzione del punto di interruzione.  
  
 `pProgram`  
 Il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta l'applicazione in cui si è verificato l'errore del punto di interruzione.  
  
 `pThread`  
 Il [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread su cui è in esecuzione l'applicazione che ha generato l'errore del punto di interruzione.  
  
 `bstrMessage`  
 Stringa contenente un messaggio di avviso o errore risultanti da questo risoluzione degli errori.  
  
 `dwType`  
 Un valore di [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) enumerazione che specifica il tipo di errore del punto di interruzione.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita dal [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)