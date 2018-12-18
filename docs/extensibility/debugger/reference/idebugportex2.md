---
title: IDebugPortEx2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6742b18c426c193716151e43cdd5b277c387e4c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportex2"></a>IDebugPortEx2
Questa interfaccia consente la sessione di debug il controllo di gestione (SDM), i programmi e i processi in esecuzione su una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia sullo stesso oggetto che implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate SDM [QueryInterface](/cpp/atl/queryinterface) sul `IDebugPort2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortEx2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Avvia un file eseguibile.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Riprende l'esecuzione di un processo.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se un processo può essere terminato.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Interrompe un processo.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ottiene l'ID del processo della porta di se stesso.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ottiene un'applicazione associata a un nodo di programma.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è in genere privata tra i SDM e il fornitore della porta personalizzata.  
  
 Se si desidera, un motore di debug (DE) è possibile visualizzare per l'interfaccia del [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia passata al [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) e utilizzare [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) per avviare il programma. Tuttavia, non è un requisito, e un Germania può effettuare qualsiasi necessarie per avviare il programma di richiesta.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)