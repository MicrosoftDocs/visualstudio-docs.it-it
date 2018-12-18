---
title: IDebugProcessSecurity::GetUserName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94fcc74943deb33e7f98ba24e9d7389a9d5746fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ottiene il nome utente dal fornitore porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrUserName`  
 [out] Stringa contenente il nome utente.  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK`. In caso contrario viene restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 `GetUserName` Restituisce il nome utente visualizzato nel **nome utente** colonna del **Connetti a processo** finestra di dialogo. Per visualizzare il **Connetti a processo** nella finestra di dialogo fare clic su **Connetti a processo** sul **strumenti** dal menu di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)