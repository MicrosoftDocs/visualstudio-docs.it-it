---
description: Questo metodo informa il processo che una sessione non sta più eseguendo il debug del processo.
title: IDebugProcessEx2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5ad25fe6461f1df89ada83623ab4e28194ca207
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076329"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Questo metodo informa il processo che una sessione non sta più eseguendo il debug del processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametri
`pSession`\
in Valore che identifica in modo univoco la sessione da cui scollegare il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'interfaccia passata deve `pSession` essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug della sessione che originariamente era collegata a questo processo; nessuno dei metodi nell'interfaccia fornita è funzionante.

## <a name="see-also"></a>Vedi anche
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
