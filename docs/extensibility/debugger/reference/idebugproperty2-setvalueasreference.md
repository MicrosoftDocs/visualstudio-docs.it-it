---
description: Imposta il valore di questa proprietà sul valore del riferimento specificato.
title: 'IDebugProperty2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b370b4caa43ce6522b415233714eb15899b3051
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064774"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Imposta il valore di questa proprietà sul valore del riferimento specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametri
`rgpArgs`\
in Matrice di argomenti da passare al setter della proprietà del codice gestito. Se il metodo di impostazione della proprietà non accetta argomenti o se questo oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) non fa riferimento a tale setter di proprietà, `rgpArgs` deve essere un valore null. Questo parametro è in genere un valore null.

`dwArgCount`\
in Numero di argomenti nella `rgpArgs` matrice.

`pValue`\
in Un riferimento, sotto forma di oggetto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , al valore da usare per impostare questa proprietà.

`dwTimeout`\
in Tempo necessario per impostare il valore, in millisecondi. Un valore tipico è `INFINITE` . Ciò influiscono sull'intervallo di tempo che può assumere qualsiasi possibile valutazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore, in genere uno dei seguenti:

|Errore|Descrizione|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|L'impostazione del valore da un riferimento non è supportata.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Il valore non può essere impostato, perché questa proprietà fa riferimento a un metodo.|
|`E_SETVALUE_VALUE_IS_READONLY`|Il valore è di sola lettura e non può essere impostato.|
|`E_NOTIMPL`|Il metodo non è implementato.|

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
