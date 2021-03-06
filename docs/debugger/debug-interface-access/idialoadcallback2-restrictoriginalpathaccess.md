---
description: Determina se è corretto cercare un file con estensione PDB nella directory di debug originale.
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7af6794b57dfe5efe8d2e85f8e74febcede5ef23
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157427"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina se è corretto cercare un file con estensione PDB nella directory di debug originale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Qualsiasi codice restituito diverso da `S_OK` impedisce la ricerca di un file con estensione PDB nella directory di debug originale. La directory di debug originale è il percorso del file di simboli compilato nell'eseguibile quando il debug è attivato. Questo percorso non corrisponde necessariamente al percorso in cui è presente il file eseguibile.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
