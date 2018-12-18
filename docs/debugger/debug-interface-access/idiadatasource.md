---
title: IDiaDataSource | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 51a277d9ff1bf190aa87d7c4e9d8d852f8c38323
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasource"></a>IDiaDataSource
Avvia l'accesso a un'origine dei simboli di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaDataSource`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera il nome del file per l'ultimo errore di caricamento.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Viene aperto e prepara un file di database (con estensione pdb) del programma come un'origine dati di debug.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Apre e verifica che il file del database (con estensione pdb) corrisponda alle informazioni di firma fornite. Prepara il file con estensione PDB come un'origine dati di debug.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Viene aperto e prepara i dati di debug associati al file.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara i dati di debug archiviati in un file di programma (PDB) di database tramito un flusso di dati in memoria.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Apre una sessione per eseguire query sui simboli.|  
  
## <a name="remarks"></a>Note  
 Una chiamata a uno dei metodi load del `IDiaDataSource` viene visualizzata l'interfaccia di origine del simbolo. Una chiamata al [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) metodo restituisce un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia che supporta query sull'origine dati. Se il metodo load restituisce un errore relativo al file il [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) metodo restituisce il valore contiene il nome del file associato all'errore.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta chiamando il `CoCreateInstance` funzione con l'identificatore di classe `CLSID_DiaSource` e l'ID di interfaccia di `IID_IDiaDataSource`. Nell'esempio viene illustrato come questa interfaccia viene ottenuta.  
  
## <a name="example"></a>Esempio  
  
```C++  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)