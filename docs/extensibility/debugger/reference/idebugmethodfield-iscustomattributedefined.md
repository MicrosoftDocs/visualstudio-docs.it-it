---
title: IDebugMethodField::IsCustomAttributeDefined | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8515fd9fc9914daa7f28f876777dd5eb26ac14c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Determina se è stato definito un attributo personalizzato specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCustomAttributeName`  
 [in] Stringa contenente il nome dell'attributo personalizzato da trovare.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce che S_OK se l'attributo personalizzato viene definito per questo metodo, in caso contrario restituisce S_FALSE.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)