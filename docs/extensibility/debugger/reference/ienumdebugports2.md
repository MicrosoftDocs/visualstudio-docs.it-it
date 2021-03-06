---
description: Questa interfaccia enumera le porte di un fornitore di computer o di porte.
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66598460a48c960b78cb89315fff6bd7ac9a845e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064592"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Questa interfaccia enumera le porte di un fornitore di computer o di porte.

## <a name="syntax"></a>Sintassi

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un elenco di porte create dal fornitore. Visual Studio implementa questa interfaccia per supportare il proprio fornitore di porte.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) per ottenere questa interfaccia che rappresenta un elenco di porte create dal fornitore della porta. Chiamare [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) per ottenere questa interfaccia che rappresenta un elenco di porte salvate su disco.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IEnumDebugPorts2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Recupera un numero specificato di porte in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Ignora un numero specificato di porte in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Ottiene il numero di porte in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio usa questa interfaccia per facilitare la compilazione di un elenco di porte usate per la connessione ai processi.

 In genere, un motore di debug non utilizza questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
