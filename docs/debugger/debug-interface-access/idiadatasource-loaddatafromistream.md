---
title: 'Idiadatasource:: Loaddatafromistream | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2421e25c51d005a069de316d1d465eca80a0432b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Prepara i dati di debug archiviati in un file di programma (PDB) di database tramito un flusso di dati in memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pIStream  
 [in] Un <xref:IStream> oggetto che rappresenta il flusso di dati da utilizzare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_PDB_FORMAT|Tentativo di accedere a un file con formato obsoleto.|  
|E_INVALIDARG|Invalidparameter.|  
|E_UNEXPECTED|Origine dati è già stata preparata.|  
  
## <a name="remarks"></a>Note  
 In questo modo i dati di debug per un file eseguibile deve essere ottenuta dalla memoria tramite un <xref:IStream> oggetto.  
  
 Per caricare un file con estensione pdb senza convalida, utilizzare il [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodo.  
  
 Per convalidare il file con estensione pdb sulla base dei criteri specifici, utilizzare il [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodo.  
  
 Per ottenere l'accesso per il processo di caricamento di dati (tramite un meccanismo di callback), utilizzare il [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)