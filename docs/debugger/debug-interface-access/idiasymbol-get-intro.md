---
description: Recupera un flag che specifica se la funzione è una funzione virtuale introduttiva.
title: IDiaSymbol::get_intro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad2e791995f4edc1b09655640bc339d577f7f37d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160876"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Recupera un flag che specifica se la funzione è una funzione virtuale introduttiva.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
`pRetVal`

out Restituisce `TRUE` se la funzione è un'introduzione virtuale; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="example"></a>Esempio

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Sia `A::f1` che `B::f1` sono funzioni virtuali, ma `A::f1` è il virtuale introduttivo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
