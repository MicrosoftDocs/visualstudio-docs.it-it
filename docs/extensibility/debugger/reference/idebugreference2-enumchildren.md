---
title: IDebugReference2::EnumChildren | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::EnumChildren
helpviewer_keywords: IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d30838a353f5bf113cc403a8caae6486c595183
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Ottenere un elenco di elementi figlio selezionati di un riferimento. Riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di flag dal [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumerazione che specifica i campi in enumerati [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture sono da compilare.  
  
 `dwRadix`  
 [in] La radice da utilizzare per la formattazione di eventuali informazioni numeriche.  
  
 `dwAttribFilter`  
 [in] Una combinazione di flag dal [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumerazione utilizzata come filtro in combinazione con il `pszNameFilter` parametro per selezionare le strutture sono da enumerare.  
  
 `pszNameFilter`  
 [in] Stringa che specifica un filtro, ad esempio "MyX", utilizzato in combinazione con il `dwAttribFilter` parametro per selezionare le strutture da enumerare.  
  
 `dwTimeout`  
 [in] Tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per un'attesa indefinita.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) oggetto che contiene un elenco delle proprietà figlio richiesto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)