---
description: Recupera un numero specificato di tabelle nella sequenza di enumerazione.
title: 'IDiaEnumTables:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdc207633a083e841221e3c6ca527c7ffb3dbcf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157882"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Recupera un numero specificato di tabelle nella sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 `celt`

in Numero di tabelle nell'enumeratore da recuperare.

 `rgelt`

out Matrice che deve essere compilata con gli oggetti [IDiaTable](../../debugger/debug-interface-access/idiatable.md) che rappresentano le tabelle desiderate.

 `pceltFetched`

out Restituisce il numero di tabelle nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altre tabelle. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
