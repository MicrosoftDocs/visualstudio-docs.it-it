---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99b57aece9b835ac1f2277fdd626a9fdff7b903f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916973"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Questa interfaccia consente la sessione di debug manager (SDM) connettersi a un programma e il nodo di programma associato a un programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sull'oggetto stesso come il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per permettere a connettersi a un programma mentre allo stesso tempo consentire il fornitore della porta tenere traccia di tutte le sessioni collegato per il modello SDM il programma. Il fornitore della porta personalizzate possa implementare questa interfaccia se sceglie.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Le chiamate SDM [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProgram2` interfaccia per ottenere questa interfaccia per tenere traccia delle sessioni che sono associati ai programmi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramEx2`.

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Connette un programma a una sessione.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ottiene il nodo di programma associato a un programma.|

## <a name="remarks"></a>Note
 Questa interfaccia è privata tra il modello SDM e il programma.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)