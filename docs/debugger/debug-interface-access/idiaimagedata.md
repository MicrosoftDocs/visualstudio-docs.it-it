---
title: IDiaImageData | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fae8401d7702351e4d51d8b8d485ece87a9478b9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaimagedata"></a>IDiaImageData
Espone i dettagli degli offset di posizione e la memoria base del modulo o immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaImageData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaImageData`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Recupera la posizione nella memoria virtuale del modulo relativo all'applicazione.|  
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Recupera la posizione nella memoria virtuale dell'immagine.|  
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Recupera la posizione di memoria in cui l'immagine deve essere basata.|  
  
## <a name="remarks"></a>Note  
 Alcuni flussi di debug (XDATA, PDATA) contengono copie dei dati archiviati anche nell'immagine. Questi flussi di dati in oggetti è possibile eseguire query per il `IDiaImageData` interfaccia. Vedere la sezione "Note per i chiamanti" in questo argomento per informazioni dettagliate.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando `QueryInterface` su un [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) oggetto. Si noti che non tutti debug flussi supporto di `IDiaImageData` interfaccia. Ad esempio, attualmente supportano solo i flussi XDATA e PDATA il `IDiaImageData` interfaccia.  
  
## <a name="example"></a>Esempio  
 Questo esempio cerca tutti i flussi di debug per qualsiasi flusso che supporta il `IDiaImageData` interfaccia. Se viene trovato un flusso di questo tipo, viene visualizzati alcune informazioni sul flusso.  
  
```C++  
void ShowImageData(IDiaSession *pSession)  
{  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumDebugStreams> pStreamsList;  
        HRESULT hr;  
  
        hr = pSession->getEnumDebugStreams(&pStreamsList);  
        if (SUCCEEDED(hr))  
        {  
            LONG numStreams = 0;  
            hr = pStreamsList->get_Count(&numStreams);  
            if (SUCCEEDED(hr))  
            {  
                ULONG fetched = 0;  
                for (LONG i = 0; i < numStreams; i++)  
                {  
                    CComPtr<IDiaEnumDebugStreamData> pStream;  
                    hr = pStreamsList->Next(1,&pStream,&fetched);  
                    if (fetched == 1)  
                    {  
                        CComPtr<IDiaImageData> pImageData;  
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),  
                                                     (void **)&pImageData);  
                        if (SUCCEEDED(hr))  
                        {  
                            CComBSTR name;  
                            hr = pStream->get_name(&name);  
                            if (SUCCEEDED(hr))  
                            {  
                                wprintf(L"Stream %s:\n",(BSTR)name);  
                            }  
                            else  
                            {  
                                wprintf(L"Failed to get name of stream\n");  
                            }  
  
                            ULONGLONG imageBase = 0;  
                            if (pImageData->get_imageBase(&imageBase) == S_OK)  
                            {  
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);  
                            }  
  
                            DWORD relVA = 0;  
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)  
                            {  
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);  
                            }  
  
                            ULONGLONG va = 0;  
                            if (pImageData->get_virtualAddress(&va) == S_OK)  
                            {  
                                wprintf(L"  virtual address = 0x%0I64x\n", va);  
                            }  
                        }  
                    }  
                }  
            }  
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
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)