---
description: Recupera il tipo di piattaforma per cui è stato compilato modulo.
title: 'IDiaSymbol:: get_platform | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 268fdb3d3e54518a05d2e8f0fe49da86dc08f114
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161928"
---
# <a name="idiasymbolget_platform"></a>IDiaSymbol::get_platform
Recupera il tipo di piattaforma per cui è stato compilato modulo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_platform ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un valore dall'enumerazione [CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) enumerazione che specifica il tipo di piattaforma per cui è stato compilato modulo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)
