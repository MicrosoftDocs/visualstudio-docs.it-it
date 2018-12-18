---
title: IDiaEnumSectionContribs | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs interface
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47577b3a2abfef3b6c6741d2e25af418318340ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsectioncontribs"></a>IDiaEnumSectionContribs
Enumera i vari contributi sezione contenuti nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumSectionContribs`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumSectionContribs::get__NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Recupera il [interfaccia IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versione di questo enumeratore.|  
|[IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|Recupera il numero dei contributi di sezione.|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Recupera i contributi di sezione tramite un indice.|  
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|Recupera un numero specificato di contributi di sezione nella sequenza di enumerazione.|  
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|Ignora un numero specificato di contributi di sezione in una sequenza di enumerazione.|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
  
## <a name="remarks"></a>Note  
  
## <a name="note-for-callers"></a>Nota per i chiamanti  
 Questa interfaccia da ottenere il [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metodo. Vedere l'esempio per informazioni dettagliate.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere (il `GetEnumSectionContribs` funzione) e utilizzare (il `ShowSectionContribs` (funzione)) di `IDiaEnumSectionContribs` interfaccia. Per un esempio più completo dei contributi di sezione, vedere il [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) interfaccia.  
  
```C++  
  
      IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);  
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
  
void ShowSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pEnumSectionContribs;  
  
    pEnumSectionContribs = GetEnumSectionContribs(pSession);  
    if (pSectionContrib != NULL)  
    {  
        IDiaSectionContrib* pSectionContrib;  
        ULONG celt = 0;  
  
        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintSectionContrib(pSectionContrib, pSession);  
            pSectionContrib->Release();  
        }  
        pSectionContrib->Release();   
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)