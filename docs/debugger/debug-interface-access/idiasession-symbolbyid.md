---
description: Recupera un simbolo in base al relativo identificatore univoco.
title: IDiaSession::symbolById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 979825cd3e62c97334d55676b3bf32bf874f8445
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147604"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Recupera un simbolo in base al relativo identificatore univoco.

## <a name="syntax"></a>Sintassi

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametri
`id`

in Identificatore univoco.

`ppSymbol`

out Restituisce un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il simbolo recuperato.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
L'identificatore specificato è un valore univoco usato internamente dal DIA SDK per rendere univoci tutti i simboli.

Questo metodo può essere usato, ad esempio, per recuperare il simbolo che rappresenta il tipo di un altro simbolo (vedere l'esempio).

## <a name="example"></a>Esempio
In questo esempio viene recuperato un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il tipo di un altro simbolo. Questo esempio illustra come usare il `symbolById` metodo nella sessione. Un approccio più semplice consiste nel chiamare il metodo [IDiaSymbol:: get_Type](../../debugger/debug-interface-access/idiasymbol-get-type.md) per recuperare direttamente il simbolo del tipo.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
