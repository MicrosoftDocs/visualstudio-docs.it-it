---
title: IDebugReference2::GetReferenceInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a40211c49f5255dba608d38529f7c56ac990e671
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Ottiene il [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura che descrive un riferimento. Riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di flag dal [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumerazione che determinano i campi per la compilazione [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura.  
  
 `nRadix`  
 [in] La radice da utilizzare per la formattazione di eventuali informazioni numeriche.  
  
 `dwTimeout`  
 [in] Tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per un'attesa indefinita.  
  
 `rgpArgs`  
 [in] Matrice di [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetti. Riservato per utilizzi futuri; impostare un valore null.  
  
 `dwArgCount`  
 [in] Il numero di argomenti di riferimento nel `rgpArgs` matrice. Riservato per utilizzi futuri; Impostare su 0.  
  
 `pReferenceInfo`  
 [out] Oggetto [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura che viene compilato con una descrizione della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)