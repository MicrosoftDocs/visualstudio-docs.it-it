---
title: IDebugSymbolProvider::GetTypeByName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetTypeByName method
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 565972b0f1f7d1f2e5e2ffd751cba60621fe284d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovidergettypebyname"></a>IDebugSymbolProvider::GetTypeByName
Questo metodo esegue il mapping a un tipo di simbolo un nome di simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeByName(   
   LPCOLESTR     pszClassName,  
   NAME_MATCH    nameMatch,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeByName(  
   string          pszClassName,   
   NAME_MATCH      nameMatch,   
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszClassName`  
 [in] Il nome del simbolo.  
  
 `nameMatch`  
 [in] Seleziona il tipo di corrispondenza, ad esempio distinzione maiuscole/minuscole. Un valore di [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumerazione.  
  
 `ppField`  
 [out] Restituisce il tipo di simbolo come un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è una versione generica di [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)