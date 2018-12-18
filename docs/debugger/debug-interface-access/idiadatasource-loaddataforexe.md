---
title: 'Idiadatasource:: Loaddataforexe | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ce90f3f46b040662f0b0dc1026dbbed0b5c1166
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Viene aperto e prepara i dati di debug associati al file.exe/.dll.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 eseguibile  
 [in] Percorso del file .exe o DLL.  
  
 searchPath  
 [in] Percorso alternativo per cercare i dati di debug.  
  
 pCallback  
 [in] Un `IUnknown` interfaccia per un oggetto che supporta un'interfaccia di callback di debug, ad esempio il [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), e/o [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfacce.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente vengono illustrati alcuni dei codici di errore possibili per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Impossibile aprire il file o il file di formato non è valido.|  
|E_PDB_FORMAT|Tentativo di accedere a un file con formato obsoleto.|  
|E_PDB_INVALID_SIG|Firma non corrisponde.|  
|E_PDB_INVALID_AGE|Non corrisponde all'età.|  
|E_INVALIDARG|Parametro non valido.|  
|E_UNEXPECTED|Origine dati è già stata preparata.|  
  
## <a name="remarks"></a>Note  
 L'intestazione di debug del file.exe/.dll denomina il percorso di dati di debug associate.  
  
 Questo metodo legge l'intestazione di debug e quindi Cerca e prepara i dati di debug. Lo stato di avanzamento della ricerca, facoltativamente, potrà essere segnalato e controllata tramite callback. Ad esempio, il [idialoadcallback:: Notifydebugdir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) viene richiamato quando il `IDiaDataSource::loadDataForExe` metodo consente di individuare ed elabora una directory di debug.  
  
 Il [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) e [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfacce consentono all'applicazione client di fornire metodi alternativi per la lettura dei dati dal file eseguibile file quando il file non sono accessibili direttamente attraverso i/o di file standard.  
  
 Per caricare un file con estensione pdb senza convalida, utilizzare il [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodo.  
  
 Per convalidare il file con estensione pdb sulla base dei criteri specifici, utilizzare il [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodo.  
  
 Per caricare un file con estensione pdb direttamente dalla memoria, utilizzare il [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodo.  
  
## <a name="example"></a>Esempio  
  
```C++  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [Notifydebugdir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)