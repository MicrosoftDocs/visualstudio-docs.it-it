---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 837372903dd1435c9cc5603805a85ce608481fc9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904257"
---
# <a name="idiadatasource"></a>IDiaDataSource
Avvia l'accesso a un'origine dei simboli di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaDataSource`.  
  
|Metodo|Description|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera il nome del file per l'ultimo errore di caricamento.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Viene aperto e lo prepara un file di database (con estensione pdb) del programma come un'origine dati di debug.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Si apre e verifica che il file di programma (PDB) del database corrisponda le informazioni sulla firma forniti. Prepara il file PDB come un'origine dati di debug.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Viene aperto e prepara i dati di debug associati al file.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara i dati di debug archiviati in un file di programma del database (con estensione pdb) si accede tramite un flusso di dati in memoria.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Apre una sessione per eseguire query sui simboli.|  
  
## <a name="remarks"></a>Note  
 Una chiamata a uno dei metodi load del `IDiaDataSource` all'origine simboli viene visualizzata l'interfaccia. Una chiamata riuscita per il [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) restituzione del metodo un' [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia che supporta query sull'origine dati. Se il metodo load restituisce un errore relativo al file il [Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) metodo restituisce il valore contiene il nome del file associato all'errore.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta chiamando il `CoCreateInstance` canonica con l'identificatore di classe `CLSID_DiaSource` e l'ID di interfaccia di `IID_IDiaDataSource`. Nell'esempio viene illustrato come questa interfaccia è ottenuta.  
  
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