---
description: Specifica se questo simbolo è un puntatore a un membro dati.
title: IDiaSymbol::get_isPointerToDataMember | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45dba4978f4ff06b77bb9216cc836e8eaec9f0e0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156090"
---
# <a name="idiasymbolget_ispointertodatamember"></a>IDiaSymbol::get_isPointerToDataMember
Specifica se questo simbolo è un puntatore a un membro dati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isPointerToDataMember(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un oggetto `BOOL` che specifica se questo simbolo è un puntatore a un membro dati.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
