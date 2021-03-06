---
description: Notifica al motore di debug (DE) se arrestare o meno in corrispondenza della posizione del codice corrente o semplicemente continuare l'esecuzione.
title: 'IDebugCanStopEvent2:: CanStop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc536b9a4f0bb0ce41e48c16cc85a53db11732b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088601"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motore di debug (DE) se arrestare o meno in corrispondenza della posizione del codice corrente o semplicemente continuare l'esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parametri
`fCanStop`\
in Diverso da zero ( `TRUE` ) se l'oggetto de deve arrestarsi in corrispondenza della posizione del codice corrente; in caso contrario, zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il ricevitore di questo evento chiama in genere il metodo [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) per determinare il motivo per cui il de vuole arrestare, quindi chiama il `IDebugCanStopEvent2::CanStop` metodo con la risposta appropriata.

 Se il valore di si interrompe, viene inviato un evento che descrive il motivo dell'arresto. In genere sono presenti due eventi inviati, un utente o un'interruzione del segnale rappresentata dall'interfaccia [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) e un evento del punto di interruzione rappresentato dall'interfaccia [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
