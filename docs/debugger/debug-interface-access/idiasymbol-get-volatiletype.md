---
description: Recupera un flag che specifica se il tipo di dati definito dall'utente (UDT) è volatile.
title: IDiaSymbol::get_volatileType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 27d2f1a49b55fd7006aa69f40e532356aded64b0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161711"
---
# <a name="idiasymbolget_volatiletype"></a>IDiaSymbol::get_volatileType
Recupera un flag che specifica se il tipo di dati definito dall'utente (UDT) è volatile.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_volatileType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se il tipo definito dall'utente è volatile; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 In C++, un tipo definito dall'utente può essere contrassegnato con la `volatile` parola chiave, che indica che il contenuto non può essere considerato esistente da un accesso a quello successivo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
