---
description: Specifica il tipo di campo contenuto in un oggetto IDebugField.
title: FIELD_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2476b819d940b5fb6014d00e1bdf920f02a46696
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085208"
---
# <a name="field_kind"></a>FIELD_KIND
Specifica il tipo di campo contenuto in un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Sintassi

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>Campi
`FIELD_KIND_TYPE`\
Indica che il campo è solo un tipo.

`FIELD_KIND_SYMBOL`\
Indica che il campo è un simbolo, con tipo, nome e altre informazioni.

`FIELD_TYPE_PRIMITIVE`\
Indica che il campo è un tipo di dati primitivo.

`FIELD_TYPE_STRUCT`\
Indica che il campo è una struttura.

`FIELD_TYPE_CLASS`\
Indica che il campo è una classe.

`FIELD_TYPE_INTERFACE`\
Indica che il campo è un'interfaccia.

`FIELD_TYPE_UNION`\
Indica che il campo è un'Unione.

`FIELD_TYPE_ARRAY`\
Indica che il campo è una matrice.

`FIELD_TYPE_METHOD`\
Indica che il campo è un metodo.

`FIELD_TYPE_BLOCK`\
Indica che il campo è un blocco.

`FIELD_TYPE_POINTER`\
Indica che il campo è un puntatore.

`FIELD_TYPE_ENUM`\
Indica che il campo è un tipo di dati enumerato.

`FIELD_TYPE_LABEL`\
Indica che il campo è un'etichetta.

`FIELD_TYPE_TYPEDEF`\
Indica che il campo è un typedef.

`FIELD_TYPE_BITFIELD`\
Indica che il campo è un bit.

`FIELD_TYPE_NAMESPACE`\
Indica che il campo è uno spazio dei nomi.

`FIELD_TYPE_MODULE`\
Indica che il campo è un modulo.

`FIELD_TYPE_DYNAMIC`\
Indica che il campo è dinamico.

`FIELD_TYPE_PROP`\
Indica che il campo è una proprietà.

`FIELD_TYPE_INNERCLASS`\
Indica che il campo è una classe interna.

`FIELD_TYPE_REFERENCE`\
Indica che il campo è un riferimento.

`FIELD_TYPE_EXTENDED`\
Riservato per utilizzi futuri.

`FIELD_SYM_MEMBER`\
Indica che il campo è un membro.

`FIELD_SYM_LOCAL`\
Indica che il campo è locale.

`FIELD_SYM_PARAMETER`\
Indica che il campo è un parametro.

`FIELD_SYM_THIS`\
Indica che il campo è il puntatore "This".

`FIELD_SYM_GLOBAL`\
Indica che il campo è globale.

`FIELD_SYM_PROP_GETTER`\
Indica che il campo recupera le proprietà.

`FIELD_SYM_PROP_SETTER`\
Indica che il campo imposta le proprietà.

`FIELD_SYM_EXTENDED`\
Riservato per utilizzi futuri.

`FIELD_KIND_MASK`\
Indica una maschera per i tipi di campo.

`FIELD_TYPE_MASK`\
Indica una maschera per i tipi di campo.

`FIELD_SYM_MASK`\
Indica una maschera per le informazioni sui simboli.

## <a name="remarks"></a>Commenti
Restituito da una chiamata al metodo [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) .

A seconda del tipo di campo, è possibile chiamare [QueryInterface](/cpp/atl/queryinterface) sull'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) per un tipo di interfaccia più specifico. Se, ad esempio, [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_METHOD` , è possibile chiamare `QueryInterface` su I `DebugField` per ottenere l'interfaccia [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) .

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
