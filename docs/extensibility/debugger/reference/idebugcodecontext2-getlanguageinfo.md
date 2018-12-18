---
title: IDebugCodeContext2::GetLanguageInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 915c6009d796209e34abc38fe5769ebdd90635d8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Ottiene le informazioni relative alla lingua per il contesto del codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrLanguage`  
 [in, out] Restituisce una stringa che contiene il nome della lingua, ad esempio "C++".  
  
 `pguidLanguage`  
 [in, out] Restituisce il GUID per la lingua di contesto del codice, ad esempio, `guidCPPLang`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Almeno uno dei parametri deve restituire un valore non null.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)