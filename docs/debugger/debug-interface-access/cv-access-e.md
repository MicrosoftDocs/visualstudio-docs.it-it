---
title: CV_access_e | Microsoft Docs
description: Ottenere informazioni sul tipo di enumerazione CV_access_e, che specifica l'ambito di visibilità (livello di accesso) dei membri in Debug Interface Access SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68dc8ca76e9250cd06009a990c0136912b0d31e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857377"
---
# <a name="cv_access_e"></a>CV_access_e
Specifica l'ambito di visibilità (livello di accesso) delle variabili e delle funzioni membro.

## <a name="syntax"></a>Sintassi

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementi
CV_private membro dispone di accesso privato.

CV_protected membro dispone di accesso protetto.

CV_public membro dispone di accesso pubblico.

## <a name="remarks"></a>Commenti
L' `friend` identificatore di accesso non è incluso in questo argomento perché viene in genere usato da funzioni non membro che hanno accesso agli elementi sia privati che protetti della classe. Usare il metodo [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) per trovare i simboli con `SymTagFriend` accesso.

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
