---
description: Riceve i callback dalla procedura di individuazione dei simboli DIA, consentendo di imporre restrizioni al processo di individuazione.
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9103157791f5ce67bb14bb05e708f7ffd87ee435
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148199"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Riceve i callback dalla procedura di individuazione dei simboli DIA, consentendo di imporre restrizioni al processo di individuazione.

## <a name="syntax"></a>Sintassi

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nell'interfaccia [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) , questa interfaccia espone i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Determina se cercare un file con estensione PDB nella directory di debug originale.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Determina se la ricerca di un file con estensione PDB è consentita nel percorso in cui si trova il file con estensione exe.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Determina se la ricerca di informazioni di debug è consentita dai file con estensione dbg.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Determina se la ricerca di file con estensione PDB è consentita nella directory radice di sistema.|

## <a name="remarks"></a>Commenti
 L'applicazione client implementa questa interfaccia e fornisce un riferimento a tale interfaccia nella chiamata al metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) . Ricordare di implementare anche tutti i metodi dell'interfaccia [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
