---
title: IDiaSourceFile | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a810d43df678d79a57a755681907b8c472fdd82d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Rappresenta un file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaSourceFile`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Recupera un valore di chiave di numeri interi semplice che è univoco per questa immagine.|  
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Recupera il nome di file di origine.|  
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Recupera il tipo di checksum.|  
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Recupera un enumeratore dei moduli con i numeri di riga che fa riferimento questo file.|  
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Recupera i byte di checksum.|  
  
## <a name="remarks"></a>Note  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il [idiaenumsourcefiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) o [idiaenumsourcefiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) metodi. Vedere l'esempio per informazioni dettagliate.  
  
## <a name="example"></a>Esempio  
 Questa funzione consente di visualizzare i nomi di tutti i file di origine che contribuiscono alla tabella specificata.  
  
```C++  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [Get_sourcefile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)   
 [Findfilebyid](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [Findlines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)