---
description: Ottiene il messaggio da visualizzare.
title: 'IDebugMessageEvent2:: GetMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc9b1747a504b761b369b2995dfef4c28ff3d012
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058469"
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

## <a name="parameters"></a>Parametri
`pMessageType`\
out Restituisce un valore dall'enumerazione [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) che descrive il tipo del messaggio.

`pbstrMessage`\
out Restituisce il messaggio.

`pdwType`\
out Restituisce il tipo del messaggio, utilizzando le convenzioni della funzione Win32 `MessageBox` . Per informazioni dettagliate, vedere la funzione [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) .

`pbstrHelpFileName`\
[in, out] Restituisce il nome del file della guida. Può essere un valore null (C++) o vuoto (C#) se non è presente alcun file della guida.

`pdwHelpId`\
[in, out] Restituisce l'identificatore della guida. Può essere 0 se non è presente alcuna guida associata a questo messaggio.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
