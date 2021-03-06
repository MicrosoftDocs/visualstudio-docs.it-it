---
description: Imposta il puntatore all'istruzione corrente sul contesto del codice specificato.
title: 'IDebugThread2:: SetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dd6bd027a9938b7dce855742cc351180498bb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081165"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Imposta il puntatore all'istruzione corrente sul contesto del codice specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parametri
`pStackFrame`\
Riservato per un utilizzo futuro; impostare su un valore null.

`pCodeContext`\
in Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che descrive la posizione del codice che sta per essere eseguita e il relativo contesto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati altri valori possibili.

|Valore|Descrizione|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|L'istruzione successiva non può trovarsi in un stack frame più in alto nello stack di frame.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|L'istruzione successiva non è associata ad alcun frame nello stack.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Alcuni motori di debug non possono impostare l'istruzione successiva dopo un'eccezione.|

## <a name="remarks"></a>Commenti
 Il puntatore all'istruzione indica l'istruzione o l'istruzione successiva da eseguire. Questo metodo viene usato per ritentare una riga di codice sorgente o per forzare l'esecuzione a continuare in un'altra funzione, ad esempio.

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
