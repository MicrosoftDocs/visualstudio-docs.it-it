---
description: Ottiene il contenitore globale del metodo.
title: 'IDebugMethodField:: GetGlobalContainer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e35082faf076bd0242d9dcc34552c31ba159fb08
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058378"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Ottiene il contenitore globale del metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametri
`ppClass`\
out Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta il modulo in cui è definito questo metodo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 L'oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) restituito rappresenta l'intero modulo ed è un oggetto artificiale, ovvero il modulo stesso non dispone di una classe effettiva, ma può essere rappresentato da un `IDebugClassField` oggetto, consentendo l'enumerazione e l'individuazione dei vari elementi del modulo.

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
