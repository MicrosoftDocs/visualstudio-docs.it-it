---
title: IDebugCodeContext2::GetLanguageInfo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords: IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6bb29ddf1ebbaafffc316562604d3e7b6cba8ff5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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