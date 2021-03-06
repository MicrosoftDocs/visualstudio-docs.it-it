---
description: Questo metodo converte il percorso di un oggetto o un indirizzo di memoria in un contesto di memoria.
title: 'IDebugBinder:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9fe7c0ee2d7902d24df1bdea773b4b2745a96f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067452"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Questo metodo converte il percorso di un oggetto o un indirizzo di memoria in un contesto di memoria.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametri
`pField`\
in Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive l'oggetto da individuare. Se `NULL` , usare `dwConstant` invece.

`dwConstant`\
in Un indirizzo di memoria costante, ad esempio 0x5000.

`ppMemCxt`\
out Restituisce l'interfaccia [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che rappresenta l'indirizzo dell'oggetto o l'indirizzo in memoria.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
