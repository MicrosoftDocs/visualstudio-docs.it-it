---
description: Specifica le informazioni da recuperare su un oggetto di riferimento di debug.
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913490588fcf739e9659318cb72a9ca74d6db99d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096226"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Specifica le informazioni da recuperare su un oggetto di riferimento di debug.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Campi
`DEBUGREF_INFO_NAME`\
Inizializza/usa il `bstrName` campo nella struttura.

`DEBUGREF_INFO_TYPE`\
Inizializza/usa il `bstrType` campo nella struttura.

`DEBUGREF_INFO_VALUE`\
Inizializza/usa il `bstrValue` campo nella struttura.

`DEBUGREF_INFO_ATTRIB`\
Inizializza/usa il `dwAttrib` campo nella struttura.

`DEBUGREF_INFO_REFTYPE`\
Inizializza/usa il `dwRefType` campo nella struttura.

`DEBUGREF_INFO_REF`\
Inizializza/usa il `pReference` campo nella struttura.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.

`DEBUGREF_INFO_NONE`\
Indica che non è impostato alcun flag.

`DEBUGREF_INFO_ALL`\
Indica una maschera dei flag.

## <a name="remarks"></a>Commenti
Questi flag vengono passati ai metodi [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) per indicare quali campi della struttura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) devono essere inizializzati.

Utilizzato per il `dwFields` membro della `DEBUG_REFERENCE_INFO` struttura per indicare quali campi vengono utilizzati e validi quando viene restituita la struttura.

Questi valori possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
