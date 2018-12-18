---
title: IDebugSymbolProvider::GetLanguage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1dfee6c4b05325b170efea314ccbc814b0ebc56
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Questo metodo ottiene la lingua utilizzata per compilare il codice in corrispondenza dell'indirizzo di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```csharp  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in] Un oggetto indirizzo rappresentato da un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
 `pguidLanguage`  
 [out] Restituisce un `GUID` che specifica la lingua.  
  
 `pguidLanguageVendor`  
 [out] Restituisce un `GUID` che specifica il fornitore di linguaggio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il motore di debug chiama questo metodo per ottenere le informazioni necessarie per selezionare l'analizzatore di espressioni corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)