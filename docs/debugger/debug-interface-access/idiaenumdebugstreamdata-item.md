---
title: IDiaEnumDebugStreamData::Item | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 941365dc4f999920e1a44688bdce482ed63a3dfb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
Recupera il record specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 indice  
 [in] Indice del record da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` restituito da [idiaenumdebugstreamdata:: Get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md).  
  
 cbData  
 [in] Dimensione del buffer di dati, in byte.  
  
 pcbData  
 [out] Restituisce il numero di byte restituiti. Se `data` è `NULL`, quindi `pcbData` contiene il numero totale di byte di dati disponibili nel record specificato.  
  
 dati]  
 [out] Un buffer che viene riempito con dati del record di flusso di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` per parametri non validi e se il `index` parametro è compreso nell'intervallo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [Idiaenumdebugstreamdata](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [Idiaenumdebugstreams](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [Idiaenumdebugstreamdata](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)