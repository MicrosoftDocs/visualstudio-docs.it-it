---
title: IDebugErrorEvent2::GetErrorMessage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dffd06c7342b77f1e4293d50217a0c6a468bf18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Restituisce le informazioni che consentono la costruzione di un messaggio di errore leggibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pMessageType`  
 [out] Restituisce un valore di [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumerazione, che indica il tipo di messaggio.  
  
 `pbstrErrorFormat`  
 [out] Il formato del messaggio all'utente finale (per informazioni dettagliate, vedere "la sezione Osservazioni").  
  
 `hrErrorReason`  
 [out] Il codice di errore, il messaggio è su.  
  
 `pdwType`  
 [out] Gravità dell'errore (utilizzare le costanti MB_XXX `MessageBox`, ad esempio `MB_EXCLAMATION` o `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Percorso di un file della Guida (impostato su un valore null se nessun file della Guida in linea).  
  
 `pdwHelpId`  
 [out] ID dell'argomento della Guida da visualizzare (impostato su 0 se non esiste alcun argomento della Guida).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il messaggio di errore deve essere formattato lungo le righe di `"What I was doing.  %1"`. Il `"%1"` quindi verrà sostituito dal chiamante con il messaggio di errore derivato dal codice di errore (che viene restituito in `hrErrorReason`). Il `pMessageType` parametro indica al chiamante come deve essere visualizzato il messaggio di errore finale.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)