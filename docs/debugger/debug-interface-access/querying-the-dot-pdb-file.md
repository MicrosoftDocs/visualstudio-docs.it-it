---
title: L'esecuzione di query di. Il File PDB | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b552300926ae0448aacd084b54934f03527f81e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="querying-the-pdb-file"></a>Ricerche nel file PDB
Un file di database di programma (estensione pdb) è un file binario che contiene informazioni sul debug simbolici raccolti nel corso di compilazione e collegamento del progetto e tipo. Un file PDB viene creato quando si compila un programma C/C++ con **/ZI** o **/Zi** o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] programmare con il **/debug** opzione. File oggetto contengono riferimenti nel file con estensione PDB per le informazioni di debug. Per ulteriori informazioni sui file pdb, vedere [file PDB](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). Un'applicazione di DIA è possibile utilizzare i passaggi generali seguenti per ottenere i dettagli sui diversi simboli, oggetti e gli elementi di dati all'interno di un'immagine eseguibile.  
  
### <a name="to-query-the-pdb-file"></a>Per eseguire query sul file con estensione pdb  
  
1.  Acquisire un'origine dati creando un [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interfaccia.  
  
    ```C++  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  Chiamare [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) o [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) per caricare le informazioni di debug.  
  
    ```C++  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  Chiamare [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) per aprire un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) per ottenere l'accesso alle informazioni di debug.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Utilizzare i metodi in `IDiaSession` per eseguire query per i simboli nell'origine dati.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Utilizzare il `IDiaEnum*` interfacce di enumerare e analizzare i simboli o altri elementi di informazioni di debug.  
  
    ```C++  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)