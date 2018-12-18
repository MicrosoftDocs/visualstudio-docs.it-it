---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0facdbd5da7d17061039e0a9e7faed2be3bbe4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Tentativo di determinare il motivo per cui un auto-attach non riuscita.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszUrl`  
 [in] Non è attualmente utilizzato; deve sempre essere impostato su un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Altri codici restituiti tipici sono i seguenti:  
  
|Codice|Descrizione|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Impossibile determinare perché il server remoto non è stato possibile avviare il debug.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Impossibile eseguire il debug in un server remoto, probabilmente a causa di autorizzazioni insufficienti o perché non è abilitato il verbo DEBUG.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Il server web è stato bloccato e blocca il verbo DEBUG, che è necessario abilitare il debug.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)