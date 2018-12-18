---
title: IDiaEnumDebugStreams | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams interface
ms.assetid: 611caf4f-7a5f-4aa4-b909-52feeb3cc752
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc2169ee7a4a6b703461ec580753595748e26e5a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumdebugstreams"></a>IDiaEnumDebugStreams
Enumera i vari flussi debug contenuti nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumDebugStreams : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumDebugStreams`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumDebugStreams::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreams-get-newenum.md)|Recupera il `IEnumVARIANT` versione di questo enumeratore.|  
|[IDiaEnumDebugStreams::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)|Recupera il numero di flussi di debug.|  
|[IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)|Recupera un flusso di debug tramite un indice.|  
|[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)|Recupera un numero specificato di flussi di debug nella sequenza di enumerazione.|  
|[IDiaEnumDebugStreams::Skip](../../debugger/debug-interface-access/idiaenumdebugstreams-skip.md)|Ignora un numero di flussi di debug in una sequenza di enumerazione specificato.|  
|[IDiaEnumDebugStreams::Reset](../../debugger/debug-interface-access/idiaenumdebugstreams-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumDebugStreams::Clone](../../debugger/debug-interface-access/idiaenumdebugstreams-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
  
## <a name="remarks"></a>Note  
 Il contenuto di flussi di debug è dipendente dall'implementazione e i formati di dati non sono documentati.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare il [idiasession:: Getenumdebugstreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md) per ottenere un `IDiaEnumDebugStreams` oggetto.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come accedere ai flussi di dati disponibili da questa interfaccia. Vedere il [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) interfaccia per l'implementazione del `PrintStreamData` (funzione).  
  
```C++  
void DumpAllDebugStreams( IDiaSession* pSession)  
{  
    IDiaEnumDebugStreams* pEnumStreams;  
  
    wprintf(L"\n\n*** DEBUG STREAMS\n\n");  
    // Retrieve an enumerated sequence of debug data streams  
    if(pSession->getEnumDebugStreams(&pEnumStreams) == S_OK)  
    {  
        IDiaEnumDebugStreamData* pStream;  
        ULONG celt = 0;  
  
        for(; pEnumStreams->Next(1, &pStream, &celt) == S_OK; pStream = NULL)  
        {  
            PrintStreamData(pStream);  
            pStream->Release();  
        }  
        pEnumStreams->Release();  
    }  
    else  
    {  
      wprintf(L"Failed to get any debug streams!\n");  
    }  
    wprintf(L"\n");  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)