---
title: IDebugComPlusSymbolProvider2::GetTypeFromToken | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::GetTypeFromToken
- GetTypeFromToken
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e0860ae08332f364e707dcde70b345ce4dae181
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcomplussymbolprovider2gettypefromtoken"></a>IDebugComPlusSymbolProvider2::GetTypeFromToken
Recupera un tipo di dato il relativo token.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeFromToken(  
   ULONG32       appDomain,  
   GUID          guidModule,  
   DWORD         tdToken,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeFromToken(  
   uint            appDomain,  
   Guid            guidModule,  
   uint            tdToken,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `appDomain`  
 [in] Identificatore del dominio dell'applicazione.  
  
 `guidModule`  
 [in] Identificatore univoco del modulo.  
  
 `tdToken`  
 [in] Token del tipo da recuperare.  
  
 `ppField`  
 [out] Restituisce il tipo rappresentato dal [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone il [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaccia.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetTypeFromToken(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    DWORD tdToken,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)