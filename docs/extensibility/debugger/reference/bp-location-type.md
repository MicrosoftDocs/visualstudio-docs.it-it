---
description: Specifica il tipo di posizione del punto di interruzione per una richiesta del punto di interruzione.
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bb3ea3220c6b4be74e0767f0e88ab1b46d2685c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096707"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Specifica il tipo di posizione del punto di interruzione per una richiesta del punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Campi
`BPLT_NONE`\
Non specifica alcun punto di interruzione.

`BPLT_FILE_LINE`\
Specifica il tipo di posizione del punto di interruzione come riga di file.

`BPLT_FUNC_OFFSET`\
Specifica il tipo di posizione del punto di interruzione come offset di funzione.

`BPLT_CONTEXT`\
Specifica il tipo di posizione del punto di interruzione come contesto.

`BPLT_STRING`\
Specifica il tipo di posizione del punto di interruzione sotto forma di stringa.

`BPLT_ADDRESS`\
Specifica il tipo di posizione del punto di interruzione come indirizzo.

`BPLT_RESOLUTION`\
Specifica il tipo di posizione del punto di interruzione come risoluzione.

`BPLT_CODE_FILE_LINE`\
Specifica il tipo di posizione del punto di interruzione come una riga di codice sorgente.

`BPLT_CODE_FUNC_OFFSET`\
Specifica il tipo di posizione del punto di interruzione come offset della funzione del codice.

`BPLT_CODE_CONTEXT`\
Specifica il tipo di posizione del punto di interruzione come contesto del codice.

`BPLT_CODE_STRING`\
Specifica il tipo di posizione del punto di interruzione come una stringa di codice.

`BPLT_CODE_ADDRESS`\
Specifica il tipo di posizione del punto di interruzione come indirizzo di codice.

`BPLT_DATA_STRING`\
Specifica il tipo di posizione del punto di interruzione come stringa di dati.

`BPLT_TYPE_MASK`\
Specifica una maschera di bit, in modo che il tipo di punto di interruzione possa essere estratto dal valore.

`BPLT_LOCATION_TYPE_MASK`\
Specifica una maschera di bit, in modo che il tipo di posizione del punto di interruzione possa essere estratto dal valore.

## <a name="remarks"></a>Commenti
Passato come parametro al metodo [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) .

Un tipo di posizione del punto di interruzione è costituito da un tipo di punto di interruzione e un tipo di posizione Ciò significa che un tipo di posizione del punto di interruzione non è mai solo un tipo di punto di interruzione (ad esempio, `BPT_CODE` ) o un tipo di posizione (ad esempio, `BPLT_FILE_LINE` ). Le costanti predefinite per tutti i tipi di posizione dei punti di interruzione attualmente supportati sono incluse in questa enumerazione ( `BPLT_CODE_FILE_LINE` tramite `BPLT_DATA_STRING` ).

`BPT_CODE` e `BPT_DATA` sono membri dell'enumerazione [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
