---
description: Specifica lo stile della condizione del punto di interruzione per i punti di interruzione in sospeso e associati.
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 611df036ff876e10096013070cac097bc51a8986
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085416"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Specifica lo stile della condizione del punto di interruzione per i punti di interruzione in sospeso e associati.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Campi
`BP_COND_NONE`\
Genera il punto di interruzione quando viene raggiunta la posizione del punto di interruzione. Non è stata specificata alcuna condizione del punto di interruzione.

`BP_COND_WHEN_TRUE`\
Genera il punto di interruzione solo quando l'espressione condizionale associata al punto di interruzione restituisce `true` .

`BP_COND_WHEN_CHANGED`\
Genera il punto di interruzione solo quando il valore dell'espressione condizionale associato al punto di interruzione è stato modificato rispetto alla valutazione precedente.

## <a name="remarks"></a>Commenti
Utilizzato per il `styleCondition` membro della struttura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
