---
description: Recupera un flag che specifica se la funzione contiene la gestione delle eccezioni asincrona (strutturata).
title: IDiaSymbol::get_hasEHa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d944cc5fc190be0917016adb14febf74162a0ca4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156314"
---
# <a name="idiasymbolget_haseha"></a>IDiaSymbol::get_hasEHa
Recupera un flag che specifica se la funzione contiene la gestione delle eccezioni asincrona (strutturata).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasEHa(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se la funzione presenta una gestione asincrona delle eccezioni; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 È possibile combinare la gestione delle eccezioni asincrona o strutturata con la gestione delle eccezioni in stile C++, ma è necessaria una specifica opzione del compilatore,/EHa, per abilitarla.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
