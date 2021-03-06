---
description: Ottiene la classe che racchiude questa classe.
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c59eb2559634c67b210f4fc3b4ce41743346c8ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088484"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Ottiene la classe che racchiude questa classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parametri
`ppClassField`\
out Restituisce un oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta la classe contenitore. Restituisce un valore null se non è presente alcuna classe contenitore.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
Se la classe rappresentata da questo oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) è una classe annidata, il `ppClassField` parametro restituisce un `IDebugClassField` oggetto che rappresenta la classe contenitore. Ad esempio, data questa definizione di classe:

```
class RootClass {
    class NestedClass { }
};
```

La chiamata al `GetEnclosingClass` metodo sull' `IDebugClassField` oggetto che rappresenta la `NestedClass` classe restituisce un `IDebugClassField` oggetto che rappresenta la classe `RootClass` .

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
