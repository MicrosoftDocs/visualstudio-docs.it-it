---
description: Apre e prepara un file di database di programma (con estensione pdb) come origine dati di debug.
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0766d951068c237e47f563a8d2ed5b3c84a9d74e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158260"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Apre e prepara un file di database di programma (con estensione pdb) come origine dati di debug.

## <a name="syntax"></a>Sintassi

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parametri
pdbPath

in Percorso del file con estensione pdb.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. La tabella seguente illustra i possibili valori restituiti per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Non è stato possibile aprire il file oppure è stato rilevato che il formato del file non è valido.|
|E_PDB_FORMAT|Tentativo di accedere a un file con un formato obsoleto.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|L'origine dati è già stata preparata.|

## <a name="remarks"></a>Commenti
Questo metodo carica i dati di debug direttamente da un file con estensione pdb.

Per convalidare il file con estensione PDB rispetto a criteri specifici, usare il metodo [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Per ottenere l'accesso al processo di caricamento dei dati (tramite un meccanismo di callback), usare il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Per caricare un file con estensione PDB direttamente dalla memoria, usare il metodo [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Esempio

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
