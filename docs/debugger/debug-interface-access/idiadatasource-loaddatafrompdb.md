---
title: 'Idiadatasource:: Loaddatafrompdb | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1910d54ad1a9d2964869beb4854ea97600569b7c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Viene aperto e prepara un file di database (con estensione pdb) del programma come un'origine dati di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pdbPath  
 [in] Il percorso del file PDB.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Impossibile aprire il file o rilevato che il file contiene un formato non valido.|  
|E_PDB_FORMAT|Tentativo di accedere a un file con formato obsoleto.|  
|E_INVALIDARG|Parametro non valido.|  
|E_UNEXPECTED|Origine dati è già stata preparata.|  
  
## <a name="remarks"></a>Note  
 Questo metodo carica i dati di debug direttamente da un file con estensione pdb.  
  
 Per convalidare il file con estensione pdb sulla base dei criteri specifici, utilizzare il [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodo.  
  
 Per ottenere l'accesso per il processo di caricamento di dati (tramite un meccanismo di callback), utilizzare il [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
 Per caricare un file con estensione pdb direttamente dalla memoria, utilizzare il [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodo.  
  
## <a name="example"></a>Esempio  
  
```C++  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)