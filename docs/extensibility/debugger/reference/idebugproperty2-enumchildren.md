---
title: IDebugProperty2::EnumChildren | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9631ee89dc9d241932b745db4ce094799a899bad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera un elenco degli elementi figlio della proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di flag dal [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumerazione che specifica i campi in enumerati [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture sono da compilare.  
  
 `dwRadix`  
 [in] Specifica la radice da utilizzare per la formattazione di eventuali informazioni numeriche.  
  
 `guidFilter`  
 [in] GUID del filtro utilizzato con il `dwAttribFilter` e `pszNameFilter` parametri per selezionare quali `DEBUG_PROPERTY_INFO` gli elementi figlio sono da enumerare. Ad esempio, `guidFilterLocals` i filtri per le variabili locali.  
  
 `dwAttribFilter`  
 [in] Una combinazione di flag dal [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumerazione che specifica il tipo di oggetti da enumerare, ad esempio `DBG_ATTRIB_METHOD` per tutti i metodi che possono essere elementi figlio di questa proprietà. Utilizzato in combinazione con il `guidFilter` e `pszNameFilter` parametri.  
  
 `pszNameFilter`  
 [in] Il nome del filtro utilizzato con il `guidFilter` e `dwAttribFilter` parametri per selezionare quali `DEBUG_PROPERTY_INFO` gli elementi figlio sono da enumerare. Ad esempio, impostando questo parametro per i filtri "MyX" per tutti gli elementi figlio con il nome "MyX".  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, in millisecondi di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per un'attesa indefinita.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) oggetto contenente un elenco delle proprietà figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)