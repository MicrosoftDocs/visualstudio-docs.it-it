---
description: Esegue il controllo dell'esecuzione (o smette di controllare l'esecuzione) nel thread specificato.
title: 'IDebugEngineProgram2:: WatchForThreadStep | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ddf7de557a5059a83aabdbfad7045e8dacbc71b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093834"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Esegue il controllo dell'esecuzione (o smette di controllare l'esecuzione) nel thread specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parametri
`pOriginatingProgram`\
in Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma di cui viene eseguito il ripasso.

`dwTid`\
in Specifica l'identificatore del thread da controllare.

`fWatch`\
in Diverso da zero ( `TRUE` ) significa iniziare a controllare l'esecuzione nel thread identificato da `dwTid` ; in caso contrario, zero ( `FALSE` ) indica l'arresto dell'esecuzione del controllo `dwTid` .

`dwFrame`\
in Specifica un indice di frame che controlla il tipo di passaggio. Se il valore è zero (0), il tipo di passaggio è "Esegui istruzione" e il programma dovrebbe arrestarsi ogni volta che il thread identificato da `dwTid` viene eseguito. Quando `dwFrame` è diverso da zero, il tipo di passaggio è "Esegui istruzione/routine" e il programma dovrebbe arrestarsi solo se il thread identificato da `dwTid` viene eseguito in un frame il cui indice è uguale o superiore nello stack rispetto a `dwFrame` .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando la gestione del debug della sessione (SDM) esegue il passaggio di un programma, identificato dal `pOriginatingProgram` parametro, invia una notifica a tutti gli altri programmi collegati chiamando questo metodo.

 Questo metodo è applicabile solo all'esecuzione dello stesso thread.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
