---
description: Questa struttura rappresenta un indirizzo relativo a un puntatore this (me in Visual Basic).
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe63edeed68bc50aae0062f171f66c8a9203ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070674"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Questa struttura rappresenta un indirizzo relativo a un `this` puntatore ( `Me` in Visual Basic).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Members
 `dwOffset`\
 Offset di byte da una posizione di base (ad esempio, inizio di una classe vtable).

 `dwBitOffset`\
 Offset in bit da una posizione di base (sempre 0 a meno che non faccia riferimento a un campo di bit).

 `dwBitLength`\
 Numero di bit che rappresentano l'indirizzo, sempre 0, a meno che non faccia riferimento a un campo di bit.

## <a name="remarks"></a>Commenti
 Questa struttura fa parte dell'Unione nella struttura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando il `dwKind` campo della `DEBUG_ADDRESS_UNION` struttura è impostato su `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (un valore dell'enumerazione [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
