---
description: Questa interfaccia viene usata dal motore di debug (DE) per inviare un messaggio a Visual Studio che richiede una risposta da parte dell'utente.
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5593e822b974ddb7c666f622192e3e4630b7222
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058430"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Questa interfaccia viene usata dal motore di debug (DE) per inviare un messaggio a Visual Studio che richiede una risposta da parte dell'utente.

## <a name="syntax"></a>Sintassi

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per inviare un messaggio a Visual Studio che richiede una risposta dell'utente. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia.

 L'implementazione di questa interfaccia deve comunicare la chiamata di [Seresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) di Visual Studio a de. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi DE oppure l'oggetto che implementa questa interfaccia potrebbe contenere un riferimento a DE e richiamarlo alla DE con la risposta passata a `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per visualizzare un messaggio all'utente che richiede una risposta. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugMessageEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ottiene il messaggio da visualizzare.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Imposta la risposta, se presente, dalla finestra di messaggio.|

## <a name="remarks"></a>Commenti
 Il DE utilizzerà questa interfaccia se richiede una risposta specifica da parte dell'utente per un determinato messaggio. Se ad esempio il valore DE ottiene un messaggio "accesso negato" dopo un tentativo di connessione remota a un programma, il DE Invia questo messaggio specifico a Visual Studio in un `IDebugMessageEvent2` evento con lo stile della finestra di messaggio `MB_RETRYCANCEL` . Ciò consente all'utente di ritentare o annullare l'operazione di connessione.

 Il DE specifica come deve essere gestito questo messaggio seguendo le convenzioni della funzione Win32 `MessageBox` (vedere [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) per informazioni dettagliate).

 Usare l'interfaccia [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) per inviare messaggi a Visual Studio che non richiedono una risposta da parte dell'utente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
