---
description: Questa struttura rappresenta un elemento di matrice all'interno di una matrice.
title: METADATA_ADDRESS_ARRAYELEM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 319b10658950eb5c7e9f8972e6af8f9f5146980d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091487"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM

Questa struttura rappresenta un elemento di matrice all'interno di una matrice.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {
    _mdToken tokMethod;
    DWORD    dwIndex;
} METADATA_ADDRESS_ARRAYELEM;
```

```csharp
public struct METADATA_ADDRESS_ARRAYELEM {
    public int  tokMethod;
    public uint dwIndex;
}
```

## <a name="members"></a>Members

`tokMethod`\
ID della matrice di cui fa parte questo elemento.

[C++] `_mdToken` è un oggetto `typedef` per un oggetto a 32 bit `int` .

`dwIndex`\
Indice di questo elemento all'interno della matrice.

## <a name="remarks"></a>Commenti
Questa struttura fa parte dell'Unione nella struttura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il `dwKind` campo della `DEBUG_ADDRESS_UNION` struttura è impostato su `ADDRESS_KIND_ARRAYELEM` (un valore dell'enumerazione [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
