---
description: 'IDiaFrameData:: get_allocatesBasePointer recupera un flag che indica se il puntatore di base è allocato per il codice in questo intervallo di indirizzi.'
title: 'IDiaFrameData:: get_allocatesBasePointer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fce5e5dbd12be7bae6ba1937b30c8a5d62de3ec
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157748"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Recupera un flag che indica se il puntatore di base è allocato per il codice in questo intervallo di indirizzi. Questo metodo è deprecato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se viene allocato un puntatore di base. in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Questa proprietà deve essere usata solo dal codice che ha avuto accesso in precedenza FPO_DATA o quando la stringa di programma restituita dal metodo [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) è `NULL` . In caso contrario, la stringa di programma contiene tutte le informazioni necessarie per calcolare i valori di registro precedenti.

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
