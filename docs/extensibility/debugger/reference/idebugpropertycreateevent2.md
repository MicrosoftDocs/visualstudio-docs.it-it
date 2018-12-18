---
title: IDebugPropertyCreateEvent2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPropertyCreateEvent2
helpviewer_keywords: IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0557fd39d21415dfddb1a571c4f9e6ee69badf10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) quando viene creata una proprietà che è associata a un documento specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per segnalare che è stata creata una proprietà. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia. Questa interfaccia viene implementata, se la Germania ha creato una proprietà associata a uno script che è stato caricato o creato e se lo script deve essere visualizzato nell'IDE.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento di report che è stata creata una proprietà. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente viene illustrato il metodo di `IDebugPropertyCreateEvent2` interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ottiene la nuova proprietà.|  
  
## <a name="remarks"></a>Note  
 Se una proprietà dispone di un documento specifico o script associato, la Germania può inviare l'evento per il SDM per aggiornare il **documenti Script** finestra con il nome del documento. Chiamerà il SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con l'argomento `guidDocument` per recuperare un `VARIANT` contenente un [IUnknown](/cpp/atl/iunknown) puntatore. Chiamerà il SDM [QueryInterface](/cpp/atl/queryinterface) su questo puntatore per recuperare il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia che viene utilizzato per aggiornare il **documenti Script** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)