---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c2b06e8d89405b38afe2b740ce860a78bc46cc
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661827"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Specifica le opzioni di ricerca per i nomi di simboli e file.

## <a name="syntax"></a>Sintassi

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Elementi
`nsNone` Non è stata specificata alcuna opzione.

`nsfCaseSensitive`Applica una corrispondenza del nome con distinzione tra maiuscole e minuscole.

`nsfCaseInsensitive`Applica una corrispondenza con il nome senza distinzione tra maiuscole e minuscole.

`nsfFNameExt`Considera i nomi come percorsi e applica un nome nomefile. EXT corrispondente.

`nsfRegularExpression`Applica una corrispondenza del nome con distinzione tra maiuscole e minuscole utilizzando asterischi (*) e punti interrogativi (?) come caratteri jolly. Altri caratteri di espressione regolare comuni non sono supportati.

`nsfUndecoratedName`Si applica solo ai simboli con nomi non decorati e decorati.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono passati ai metodi seguenti:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
