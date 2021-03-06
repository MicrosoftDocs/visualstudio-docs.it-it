---
description: La struttura METADATA_TYPE specifica le informazioni su un tipo di campo tratto dai metadati.
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a76e051e146985338564d497323b6232b35a4a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079852"
---
# <a name="metadata_type"></a>METADATA_TYPE
Questa struttura specifica le informazioni su un tipo di campo tratto dai metadati.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parametri
 `ulAppDomainID`\
 ID dell'applicazione da cui è arrivato il simbolo. Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.

 `guidModule`\
 GUID del modulo che contiene questo campo.

 `tokClass`\
 ID del token di metadati di questo tipo.

 [C++] `_mdToken` è un oggetto `typedef` per un oggetto a 32 bit `int` .

## <a name="remarks"></a>Commenti
 Questa struttura viene visualizzata come parte dell'Unione nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il `dwKind` campo della `TYPE_INFO` struttura è impostato su `TYPE_KIND_METADATA` (un valore dell'enumerazione [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

 Il `tokClass` valore è un token di metadati che identifica in modo univoco un tipo. Per informazioni dettagliate su come interpretare i bit superiori dell'ID del token di metadati, vedere l' `CorTokenType` enumerazione nel file corhdr. h in .NET Framework SDK.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
