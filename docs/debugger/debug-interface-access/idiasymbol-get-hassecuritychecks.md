---
description: Recupera un flag che specifica se la funzione modulo o è stata compilata con controlli di sicurezza con sovraccarico del buffer, ad esempio l'opzione del compilatore/GS (controllo di sicurezza del buffer)).
title: IDiaSymbol::get_hasSecurityChecks | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56f337a84081aa8c0282efcf07b70f30d98da15e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162068"
---
# <a name="idiasymbolget_hassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Recupera un flag che specifica se la funzione modulo o è stata compilata con controlli di sicurezza con sovraccarico del buffer, ad esempio l'opzione del compilatore [/GS (controllo di sicurezza del buffer)](/cpp/build/reference/gs-buffer-security-check) .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se la funzione dispone di controlli di sicurezza. in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (controllo sicurezza buffer)](/cpp/build/reference/gs-buffer-security-check)
