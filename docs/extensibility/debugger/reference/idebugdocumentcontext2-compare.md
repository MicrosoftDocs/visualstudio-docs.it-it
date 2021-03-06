---
description: Confronta questo contesto del documento con una matrice specificata di contesti di documento.
title: 'IDebugDocumentContext2:: compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a680da6f33d3da37995eb26071c0ea5f1ddc2283
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066711"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Confronta questo contesto del documento con una matrice specificata di contesti di documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parametri
`compare`\
in Valore dell'enumerazione [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) che specifica il tipo di confronto.

`rgpDocContextSet`\
in Matrice di oggetti [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) che rappresentano i contesti di documento confrontati con.

`dwDocContextSetLen`\
in Lunghezza della matrice dei contesti di documento da confrontare.

`pdwDocContext`\
out Restituisce l'indice nella `rgpDocContextSet` matrice del primo contesto del documento che soddisfa il confronto.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stata trovata una corrispondenza. Restituisce `S_FALSE` se non è stata trovata alcuna corrispondenza. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Gli oggetti [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) passati nella matrice devono essere implementati dallo stesso motore di debug che implementa l' `IDebugDocumentContext2` oggetto su cui viene chiamato il metodo; in caso contrario, il confronto non è valido.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
