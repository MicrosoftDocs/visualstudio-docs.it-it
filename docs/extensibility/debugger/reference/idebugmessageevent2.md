---
title: IDebugMessageEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d0cb1f270d3d3ae77c43ea89fba5b7483e80412
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare un messaggio a Visual Studio che richiede una risposta da parte dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per inviare un messaggio a Visual Studio che richiede una risposta dell'utente. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.  
  
 L'implementazione di questa interfaccia deve comunicare la chiamata di Visual Studio di [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) per la Germania. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al messaggio del DE thread di gestione o l'oggetto che implementa questa interfaccia potrebbe contenere un riferimento per la Germania e richiamare la Germania con la risposta passata `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento per visualizzare un messaggio all'utente che richiede una risposta. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugMessageEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ottiene il messaggio da visualizzare.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Imposta la risposta, se presente, nella finestra di messaggio.|  
  
## <a name="remarks"></a>Note  
 Se richiede una risposta specifica da parte dell'utente per un determinato messaggio, la Germania utilizzerà questa interfaccia. Ad esempio, se la Germania Ottiene un messaggio "Accesso negato" dopo un tentativo di connettersi a un programma in modalità remota, la Germania invia il messaggio specifico per Visual Studio in un `IDebugMessageEvent2` evento con lo stile di finestra di messaggio `MB_RETRYCANCEL`. Ciò consente all'utente di ripetere oppure annullare l'operazione di collegamento.  
  
 La Germania specifica come il messaggio è da gestire seguendo le convenzioni della funzione Win32 `MessageBox` (vedere [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) per informazioni dettagliate).  
  
 Utilizzare il [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaccia per inviare messaggi a Visual Studio che non richiedono una risposta da parte dell'utente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)