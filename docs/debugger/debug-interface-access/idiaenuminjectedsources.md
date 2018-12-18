---
title: IDiaEnumInjectedSources | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources interface
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7467ce576e8e99213242733ca7b1cad3cb2dc98
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenuminjectedsources"></a>IDiaEnumInjectedSources
Consente di enumerare le varie origini inserite contenute nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumInjectedSources : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumInjectedSources`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumInjectedSources::get__NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Recupera il [interfaccia IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versione di questo enumeratore.|  
|[IDiaEnumInjectedSources::get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Recupera il numero di origini inserite.|  
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Recupera un'origine inserita tramite un indice.|  
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Recupera un numero di origini inserite nella sequenza di enumerazione specificato.|  
|[IDiaEnumInjectedSources::Skip](../../debugger/debug-interface-access/idiaenuminjectedsources-skip.md)|Ignora un numero di origini inserite in una sequenza di enumerazione specificato.|  
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
  
## <a name="remarks"></a>Note  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta chiamando il [idiasession:: Findinjectedsource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md) metodo con il nome di un file di origine specifico o chiamando il [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metodo con il GUID del `IDiaEnumInjectedSources` interfaccia.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere (il `GetEnumInjectedSources` funzione) e utilizzare (il `DumpAllInjectedSources` (funzione)) di `IDiaEnumInjectedSources` interfaccia. Vedere il [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) interfaccia per l'implementazione del `PrintPropertyStorage` (funzione). Per un output alternativi, vedere il [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interfaccia.  
  
```C++  
  
IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)  
{  
    IDiaEnumInjectedSources* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);  
    IDiaEnumTables*          pEnumTables = NULL;  
    IDiaTable*               pTable      = NULL;  
    ULONG                    celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
  
void DumpAllInjectedSources( IDiaSession* pSession)  
{  
    IDiaEnumInjectedSources* pEnumInjSources;  
  
    pEnumInjSources = GetEnumInjectedSources(pSession);  
    if (pEnumInjSources != NULL)  
    {  
        IDiaInjectedSource* pInjSource;  
        ULONG celt = 0;  
  
        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&  
              celt == 1)  
        {  
            IDiaPropertyStorage *pPropertyStorage;  
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),  
                                           (void **)&pPropertyStorage) == S_OK)  
            {  
                PrintPropertyStorage(pPropertyStorage);  
                pPropertyStorage->Release();  
            }  
            pInjSource->Release();  
        }  
        pEnumInjSources->Release();  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Findinjectedsource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)   
 [Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)