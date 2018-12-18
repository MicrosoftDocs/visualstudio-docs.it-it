---
title: IDiaEnumFrameData | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData interface
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c39057a77da9b459852e0b591ea8d69186ee6f8d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumframedata"></a>IDiaEnumFrameData
Enumera i vari elementi di dati di frame contenuti nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumFrameData`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumFrameData::get__NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|Recupera il `IEnumVARIANT Interface` versione di questo enumeratore.|  
|[IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|Recupera il numero di elementi frame di dati.|  
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|Recupera un elemento frame di dati tramite un indice.|  
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|Recupera un numero specificato di elementi frame di dati nella sequenza di enumerazione.|  
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|Ignora un numero specificato di elementi frame di dati in una sequenza di enumerazione.|  
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|Restituisce un intervallo di indirizzi virtuali relativi (RVA).|  
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|Restituisce un intervallo di indirizzi virtuali (VA).|  
  
## <a name="remarks"></a>Note  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia da ottenere il [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metodo. Vedere l'esempio per informazioni dettagliate.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere (il `GetEnumFrameData` funzione) e utilizzare (il `ShowFrameData` (funzione)) di `IDiaEnumFrameData` interfaccia. Vedere il [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) interfaccia per un esempio di `PrintFrameData` (funzione).  
  
```C++  
  
      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pUnknown    = NULL;  
    REFIID             iid         = __uuidof(IDiaEnumFrameData);  
    IDiaEnumTables*    pEnumTables = NULL;  
    IDiaTable*         pTable      = NULL;  
    ULONG              celt        = 0;  
  
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
  
void ShowFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;  
  
    if (pEnumFrameData != NULL)  
    {  
        IDiaFrameData* pFrameData;  
        ULONG celt = 0;  
  
        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintFrameData(pFrameData);  
            pFrameData->Release();  
        }  
        pEnumFrameData->Release();   
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** Dia2.h  
  
 **Libreria:** diaguids.lib  
  
 **DLL:** MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)