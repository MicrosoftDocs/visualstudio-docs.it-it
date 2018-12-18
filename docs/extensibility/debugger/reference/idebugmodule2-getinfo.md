---
title: IDebugModule2::GetInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8eb4f06899b7b3bc30453282463c9402e45c2aee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Ottiene informazioni su questo modulo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di flag dal [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) enumerazione che specificano quali campi della `pInfo` devono essere compilati.  
  
 `pInfo`  
 [in, out] Oggetto [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura che viene compilato con una descrizione del modulo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura contiene il nome del modulo che viene visualizzato nel **moduli** finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)