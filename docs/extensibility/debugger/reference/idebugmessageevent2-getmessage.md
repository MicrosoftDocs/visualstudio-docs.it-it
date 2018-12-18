---
title: IDebugMessageEvent2::GetMessage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a00f7019a96696b0c1bde6876697b71d96c253d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Ottiene il messaggio da visualizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pMessageType`  
 [out] Restituisce un valore di [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumerazione che descrive il tipo del messaggio.  
  
 `pbstrMessage`  
 [out] Restituisce il messaggio.  
  
 `pdwType`  
 [out] Restituisce il tipo del messaggio, utilizzando le convenzioni di Win32 `MessageBox` (funzione). Vedere il [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) funzione per i dettagli.  
  
 `pbstrHelpFileName`  
 [in, out] Restituisce il nome del file della Guida. Può essere un valore null (C++) o un valore vuoto (c#) se è presente alcun file della Guida.  
  
 `pdwHelpId`  
 [in, out] Restituisce l'identificatore della Guida. Può essere 0 se non esiste alcuna informazione della Guida associata a questo messaggio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)