---
title: IDebugSymbolProvider::GetAddressesFromPosition | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 129ed233361991f5e58a258c73838bc9739112de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Questo metodo esegue il mapping di una posizione del documento in una matrice di indirizzi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDocPos`  
 [in] Posizione del documento.  
  
 `fStatmentOnly`  
 [in] Se TRUE, limita gli indirizzi di debug per una singola istruzione.  
  
 `ppEnumBegAddresses`  
 [out] Restituisce un enumeratore per gli indirizzi iniziali di debug associata a questa istruzione o la riga.  
  
 `ppEnumEndAddresses`  
 [out] Restituisce un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumeratore per gli indirizzi di debug finale associata a questa istruzione o la riga.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Una posizione del documento in genere indica un intervallo di righe di origine. Questo metodo fornisce iniziale e quello finale debug associata a queste righe. Alcuni linguaggi consentono istruzioni che si estendono su più righe o le righe che contiene più di un'istruzione. Questo metodo fornisce un flag per limitare gli indirizzi di debug per una singola istruzione.  
  
 È possibile per una singola istruzione per disporre di più indirizzi di debug, come nel caso di modelli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)