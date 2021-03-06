---
description: Fornisce l'accesso ai record in un flusso di dati di debug.
title: IDiaEnumDebugStreamData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f94fbc365ddd913494bb0fb04f81615c0945955b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149123"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
Fornisce l'accesso ai record in un flusso di dati di debug.

## <a name="syntax"></a>Sintassi

```
IDiaEnumDebugStreamData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaEnumDebugStreamData` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Recupera la versione dell' [interfaccia IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) dell'enumeratore.|
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|Recupera il numero di record nel flusso di dati di debug.|
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|Recupera il nome del flusso di dati di debug.|
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|Recupera il record specificato.|
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Recupera il numero specificato di record dalla sequenza enumerata.|
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|Ignora un numero specificato di record in una sequenza enumerata.|
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|Reimposta l'inizio della sequenza enumerata.|
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Crea un enumeratore che contiene la stessa sequenza enumerata dell'enumeratore corrente.|

## <a name="remarks"></a>Commenti
Questa interfaccia rappresenta un flusso di record in un flusso di dati di debug. Le dimensioni e l'interpretazione di ogni record dipendono dal flusso di dati da cui deriva il record. Questa interfaccia fornisce in modo efficace l'accesso ai byte dei dati non elaborati nel file di simboli.

## <a name="notes-for-callers"></a>Note per i chiamanti
Chiamare i metodi [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) o [IDiaEnumDebugStreams:: Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) per ottenere un `IDiaEnumDebugStreamData` oggetto.

## <a name="example"></a>Esempio
 Questo esempio Mostra come accedere a un singolo flusso di dati e ai relativi record.

```C++
void PrintStreamData(IDiaEnumDebugStreamData* pStream)
{
    BSTR  wszName;
    LONG  dwElem;
    ULONG celt    = 0;
    DWORD cbData;
    DWORD cbTotal = 0;
    BYTE  data[1024];

    if(pStream->get_name(&wszName) != S_OK)
    {
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");
    }
    else
    {
        wprintf_s(L"Stream: %s", wszName);
        SysFreeString(wszName);
    }
    if(pStream->get_Count(&dwElem) != S_OK)
    {
        wprintf(L"ERROR - PrintStreamData() get_Count\n");
    }
    else
    {
        wprintf(L"(%d)\n", dwElem);
    }
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)
    {
        DWORD i;
        for (i = 0; i < cbData; i++)
        {
            wprintf(L"%02X ", data[i]);
            if(i && i % 8 == 7 && i+1 < cbData)
            {
                wprintf(L"- ");
            }
        }
        wprintf(L"| ");
        for(i = 0; i < cbData; i++)
        {
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');
        }
        wprintf(L"\n");
        cbTotal += cbData;
    }
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",
            cbTotal/dwElem, dwElem);
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
