---
description: Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare eventi di debug a gestione debug sessione (SDM).
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d00c970c522adf232f9a18b762c7d6cf3cf3b794
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084896"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare eventi di debug a gestione debug sessione (SDM).

## <a name="syntax"></a>Sintassi

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementa questa interfaccia per ricevere eventi da un motore di debug.

## <a name="notes-for-callers"></a>Note per i chiamanti
 In genere, un motore di debug riceve questa interfaccia quando SDM chiama [alleghi](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motore di debug invia eventi a SDM chiamando l' [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugEventCallback2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Invia la notifica di eventi di debug a SDM.|

## <a name="remarks"></a>Commenti
 Sebbene [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) specifichino che accettano un' `IDebugEventCallback2` interfaccia, questo non è il caso e il puntatore di interfaccia sarà sempre un valore null. Al contrario, il motore di debug deve usare l' `IDebugEventCallback2` interfaccia ricevuta nella chiamata a [alleghi](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Se un pacchetto implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) nel codice gestito, è consigliabile <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> richiamarlo sulle varie interfacce passate all' [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
