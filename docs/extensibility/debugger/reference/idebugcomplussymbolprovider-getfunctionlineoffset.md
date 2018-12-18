---
title: IDebugComPlusSymbolProvider::GetFunctionLineOffset | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetFunctionLineOffset
- GetFunctionLineOffset
ms.assetid: 51460f5a-4e98-427a-8315-27246e24fb61
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a1308b8649593b1145290a636dae88a50109647c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcomplussymbolprovidergetfunctionlineoffset"></a>IDebugComPlusSymbolProvider::GetFunctionLineOffset
Recupera l'indirizzo di una funzione che rappresenta l'offset di riga specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetFunctionLineOffset(  
   IDebugAddress*  pAddress,   
   DWORD           dwLine,   
   IDebugAddress** ppNewAddress   
);  
```  
  
```csharp  
int GetFunctionLineOffset(  
   IDebugAddress     pAddress,   
   uint              dwLine,   
   out IDebugAddress ppNewAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in] Indirizzo che rappresenta una funzione.  
  
 `dwLine`  
 [in] Riga offset dall'inizio della funzione.  
  
 `ppNewAddress`  
 [out] Nuovo indirizzo che rappresenta l'offset dall'inizio della funzione di riga.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone il [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetFunctionLineOffset(  
    IDebugAddress *pAddress,  
    DWORD dwLine,  
    IDebugAddress **ppNewAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
    DWORD dwOffset;  
    CDebugAddress* paddr = NULL;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetFunctionLineOffset);  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    // Find the first offset for dwLine in the function  
  
    IfFailGo( pModule->GetFunctionLineOffset( address.addr.addr.addrMethod.tokMethod,  
              address.addr.addr.addrMethod.dwVersion,  
              dwLine,  
              &dwOffset ) );  
  
    // Create the new Address  
  
    address.addr.addr.addrMethod.dwOffset = dwOffset;  
    IfNullGo( paddr = new CDebugAddress(address), E_OUTOFMEMORY );  
    IfFailGo( paddr->QueryInterface( __uuidof(IDebugAddress),  
                                     (void**) ppNewAddress ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetFunctionLineOffset, hr);  
    RELEASE( paddr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)