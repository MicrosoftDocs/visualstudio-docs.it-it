---
title: IDiaEnumFrameData::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fe478e503ed6e16ee570f309f91434c658ebd27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744593"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Recupera un numero specificato di elementi dati del frame nella sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

in Numero di elementi dati del frame nell'enumeratore da recuperare.

 rgelt

out Matrice di oggetti [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) da compilare con gli elementi dati del frame richiesti.

 pceltFetched

out Restituisce il numero di elementi dati del frame nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri record. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)