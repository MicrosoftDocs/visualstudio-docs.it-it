---
title: BP_RESOLUTION_DATA | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f76cba8fa2b1ea01a2cbd7670a05b449d476127b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
Viene descritto il risultato dell'associazione di un punto di interruzione dei dati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>Membri  
 `bstrDataExpr`  
 L'espressione di dati che è stato associato.  
  
 `bstrFunc`  
 Il nome della funzione è associato il punto di interruzione dei dati (se presente).  
  
 `bstrImage`  
 Il nome del modulo (ad esempio MyModule.dll) che è associato il punto di interruzione dei dati in.  
  
 `dwFlags`  
 Un valore di [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) enumerazione, che indica la modalità di implementazione il punto di interruzione dei dati.  
  
## <a name="remarks"></a>Note  
 Questa struttura è un membro del [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) struttura, che a sua volta è un membro del [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura restituita dal [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)