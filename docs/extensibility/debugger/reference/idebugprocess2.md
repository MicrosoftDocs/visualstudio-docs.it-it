---
description: Questa interfaccia rappresenta un processo in esecuzione su una porta.
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d56687cb3559b5807b488fa44dfdfc4048e4c58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081607"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Questa interfaccia rappresenta un processo in esecuzione su una porta. Se la porta è la porta locale, `IDebugProcess2` in genere rappresenta un processo fisico nel computer locale.

## <a name="syntax"></a>Sintassi

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un fornitore di porte personalizzato per gestire i programmi come un gruppo. Questa interfaccia deve essere implementata dal fornitore della porta.

 Un motore di debug implementa anche questa interfaccia se supporta l'avvio di un programma tramite [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata principalmente da gestione debug sessione (SDM) per interagire con un gruppo di programmi identificato in questo processo.

 Chiamare [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) per ottenere questa interfaccia. Questa interfaccia viene restituita anche chiamando `IDebugEngineLaunch2::LaunchSuspended` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugProcess2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ottiene una descrizione del processo.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera i programmi contenuti nel processo.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ottiene il titolo, il nome descrittivo o il nome file del processo.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ottiene l'istanza di un server del computer in cui è in esecuzione il processo.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md).|Termina il processo.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Si connette al processo.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se SDM può scollegare il processo.|
|[Scollega](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Scollega il debugger dal processo.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ottiene l'identificatore del processo di sistema.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ottiene un identificatore univoco globale per questo processo.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> DEPRECATO|Ottiene il nome della sessione che esegue il debug del processo.<br /><br /> Deprecato. DEVE sempre restituire `E_NOTIMPL` .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera i thread in esecuzione nel processo.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Richiede che il programma successivo che esegue il codice in questo processo venga arrestato.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ottiene la porta su cui è in esecuzione il processo.|

## <a name="remarks"></a>Commenti
 Un oggetto `IDebugProcess2` contiene una o più interfacce [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
