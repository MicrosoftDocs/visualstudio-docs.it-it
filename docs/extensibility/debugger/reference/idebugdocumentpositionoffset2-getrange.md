---
description: Recupera l'intervallo per la posizione del documento corrente.
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66184ba67dd0623a886ca37e28d311aebc6633bd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066347"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera l'intervallo per la posizione del documento corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parametri
`pdwBegOffset`\
[in, out] Offset per la posizione iniziale dell'intervallo. Se queste informazioni non sono necessarie, impostare questo parametro su un valore null.

`pdwEndOffset`\
[in, out] Offset per la posizione finale dell'intervallo. Se queste informazioni non sono necessarie, impostare questo parametro su un valore null.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'intervallo specificato in una posizione del documento per un punto di interruzione del percorso viene utilizzato dal motore di debug (DE) per eseguire una ricerca in avanti di un'istruzione che contribuisce effettivamente al codice. Si consideri il codice di esempio seguente:

```
Line 5: // comment
Line 6: x = 1;
```

 La riga 5 non contribuisce al programma di cui è in corso il debug. Se il debugger che imposta il punto di interruzione nella riga 5 vuole che il DE cerchi in avanti una determinata quantità per la prima riga che contribuisce al codice, il debugger specifica un intervallo che include righe candidati aggiuntive in cui un punto di interruzione può essere posizionato correttamente. Il DE, quindi, ricercherà le righe fino a trovare una riga che potrebbe accettare un punto di interruzione.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
