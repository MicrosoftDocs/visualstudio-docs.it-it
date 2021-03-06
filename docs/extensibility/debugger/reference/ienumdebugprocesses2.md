---
description: Questa interfaccia enumera i processi in esecuzione su una porta di debug.
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1272c57b58b4e2656775bf746d470a3514c886ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064540"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Questa interfaccia enumera i processi in esecuzione su una porta di debug.

## <a name="syntax"></a>Sintassi

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per fornire un elenco di processi in esecuzione su una porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IEnumDebugProcesses2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera un numero specificato di processi in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignora un numero specificato di processi in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Ottiene il numero di processi in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio usa questa interfaccia per popolare la finestra **processi** .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
