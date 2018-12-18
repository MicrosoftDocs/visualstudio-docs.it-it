---
title: IDiaTable | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e95c469bb3a1d8747a7f1dabfadec24dc991730c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiatable"></a>IDiaTable
Enumera una tabella di origine dati DIA.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaTable`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera il [interfaccia IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versione di questo enumeratore.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera il nome della tabella.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera il numero di elementi nella tabella.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera un riferimento a una particolare voce di indice.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia implementerà il `IEnumUnknown` metodi di enumerazione nello spazio dei nomi Interop. Il `IEnumUnknown` è molto più efficiente per scorrere il contenuto della tabella di interfaccia di enumerazione di [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md) e [idiatable:: Item](../../debugger/debug-interface-access/idiatable-item.md) metodi.  
  
 L'interpretazione del `IUnknown` interfaccia restituita dal `IDiaTable::Item` metodo o `Next` (metodo) (nello spazio dei nomi Interop) dipende dal tipo di tabella. Ad esempio, se il `IDiaTable` interfaccia rappresenta un elenco di origini inserite, la `IUnknown` interfaccia deve essere eseguita una query per il [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il [idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o [idiaenumtables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) metodi.  
  
 Vengono implementate le interfacce seguenti con il `IDiaTable` interfaccia (ovvero, è possibile eseguire una query il `IDiaTable` interfaccia per una delle interfacce seguenti):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Esempio  
 La prima funzione `ShowTableNames`, vengono visualizzati i nomi di tutte le tabelle nella sessione. La seconda funzione `GetTable`, esegue la ricerca di tutte le tabelle per una tabella che implementa un'interfaccia specificata. La terza funzione `UseTable`, viene illustrato come utilizzare il `GetTable` (funzione).  
  
> [!NOTE]
>  `CDiaBSTR` è una classe che esegue il wrapping di un `BSTR` e gestisce automaticamente liberando la stringa quando la creazione dell'istanza diventa esterno all'ambito.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)