---
title: IDebugTypeFieldBuilder::CreatePrimitive | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreatePrimitive
- IDebugTypeFieldBuilder::CreatePrimitive
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08394a62dc115f7bade9c417b8e39ba6b41eeb1b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319854"
---
# <a name="idebugtypefieldbuildercreateprimitive"></a>IDebugTypeFieldBuilder::CreatePrimitive
Crea un oggetto che rappresenta un tipo primitivo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreatePrimitive (
   DWORD          dwElementType,
   IDebugField ** pTypeField
);
```

```csharp
int CreatePrimitive (
   uint            dwElementType,
   out IDebugField pTypeField
);
```

## <a name="parameters"></a>Parametri
`dwElementType`\
[in] Valore di [enumerazione CorElementType](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) che rappresenta il tipo primitivo.

`pTypeField`\
[out] Restituisce l'interfaccia IDebugField per il nuovo tipo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)