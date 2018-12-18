---
title: IDebugCoreServer2::GetMachineInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetInfo
helpviewer_keywords:
- IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 76d347a40993b722b13545dd278138ce753344f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
Recupera una descrizione del computer che in cui è in esecuzione il server principale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetInfo(   
   MACHINE_INFO_FIELDS Fields,  
   MACHINE_INFO*       pMachineInfo  
);  
```  
  
```csharp  
int GetInfo(   
   enum_ MACHINE_INFO_FIELDS  Fields,  
   MACHINE_INFO[]             pMachineInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Fields`  
 [in] Una combinazione di flag dal [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) enumerazione che specificano quali campi della `pMachineInfo` devono essere compilati.  
  
 `pMachineInfo`  
 [in, out] Oggetto [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struttura che viene compilato con una descrizione della macchina.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)