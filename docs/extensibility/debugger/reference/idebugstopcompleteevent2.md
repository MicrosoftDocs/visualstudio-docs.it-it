---
title: IDebugStopCompleteEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Il motore di debug (DE) è possibile inviare questo evento facoltativo da gestore di sessione di debug (SDM) quando un programma è stato arrestato.

## <a name="syntax"></a>Sintassi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori

Questa interfaccia è stata introdotta con Visual Studio 2005. Le versioni precedenti non supportava interruzione asincrona.

[Arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM in più processi o un programma più scenari. Quando un programma invia un evento di arresto per il SDM, il SDM richiede altri programmi di arrestare.

Arresto viene utilizzato per indicare in modo asincrono SDM che un programma è stato arrestato. Informare il SDM è utile per un motore di debug interprete, in alcuni casi codice non è in esecuzione in fase di debug del programma, pertanto [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere eseguita in modo sincrono. Se un motore di debug decide di utilizzare questa notifica asincrona, deve restituire `S_ASYNC_STOP` da [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll