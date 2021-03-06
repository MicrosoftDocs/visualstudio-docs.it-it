---
description: Questa interfaccia consente a gestione debug sessione (SDM) di controllare i programmi e i processi in esecuzione su una porta.
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e26fec4b47a301bfb266f40b41fd88216ccf671f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072429"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Questa interfaccia consente a gestione debug sessione (SDM) di controllare i programmi e i processi in esecuzione su una porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto che implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
 SDM chiama [QueryInterface](/cpp/atl/queryinterface) sull' `IDebugPort2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugPortEx2` .

|Metodo|Descrizione|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Avvia un file eseguibile.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Riprende l'esecuzione di un processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se un processo può essere terminato.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termina un processo.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ottiene l'ID del processo della porta stessa.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ottiene un programma associato a un nodo di programma.|

## <a name="remarks"></a>Commenti
 Questa interfaccia è generalmente privata tra il SDM e il fornitore della porta personalizzata.

 Se lo si desidera, un motore di debug (DE) può cercare questa interfaccia sull'interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) passata a [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) e utilizzare [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) per avviare il programma. Tuttavia, questo non è un requisito e un DE può eseguire tutte le operazioni necessarie per avviare il programma di richiesta.

## <a name="requirements"></a>Requisiti
 Intestazione: portpriv. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
