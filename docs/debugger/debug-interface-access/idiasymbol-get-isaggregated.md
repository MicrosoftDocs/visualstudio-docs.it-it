---
description: Recupera un flag che specifica se il simbolo di dati fa parte di un'aggregazione o di una raccolta di simboli. il compilatore considererà i simboli aggregati come entità separate, ma fa parte di un singolo simbolo più grande.
title: IDiaSymbol::get_isAggregated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e78ec7f180ad1c719d562975377a413156bb1480
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160862"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Recupera un flag che specifica se il simbolo di dati fa parte di un'aggregazione o di una raccolta di simboli. il compilatore considererà i simboli aggregati come entità separate, ma fa parte di un singolo simbolo più grande.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se i dati fanno parte di un'aggregazione di simboli divisi da un simbolo padre; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Il metodo [IDiaSymbol:: get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) è `TRUE` per il simbolo che rappresenta l'elemento padre dei simboli aggregati.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)
