---
title: IDebugProperty2::GetPropertyInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f922731f5c595f7308f78269b8386b7da20e2398
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Ottiene il [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura che descrive una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione dei valori di [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumerazione che specifica i campi devono essere compilati nel `pPropertyInfo` struttura.  
  
 `nRadix`  
 [in] Base da utilizzare per la formattazione di eventuali informazioni numeriche.  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, in millisecondi di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per un'attesa indefinita.  
  
 `rgpArgs`  
 [in, out] Riservato per utilizzi futuri; impostare un valore null.  
  
 `dwArgCount`  
 [in] Riservato per utilizzi futuri; Impostare su zero.  
  
 `pPropertyInfo`  
 [out] Oggetto [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura che viene compilato con la descrizione della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)