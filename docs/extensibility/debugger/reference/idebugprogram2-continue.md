---
description: "IDebugProgram2:: continue continua l'esecuzione del programma da uno stato interrotto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene mantenuto e l'esecuzione del programma viene nuovamente avviata."
title: 'IDebugProgram2:: continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60f3cb4764a53d359e971020df8261d064c62e81
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076121"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua l'esecuzione del programma da uno stato interrotto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene mantenuto e l'esecuzione del programma viene nuovamente avviata.

> [!NOTE]
> Questo metodo è deprecato. Usare invece il metodo [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametri
`pThread` in Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su questo programma indipendentemente dal numero di programmi di cui è in corso il debug o dal programma che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai stata arrestata prima del completamento dell'esecuzione precedente. Ovvero, se un thread in questo programma stava eseguendo un'operazione Step-over ed è stato interrotto perché un altro programma è stato arrestato e quindi questo metodo è stato chiamato, il programma deve completare l'operazione di passaggio originale.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) a [un evento durante](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) la gestione della chiamata; in caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
