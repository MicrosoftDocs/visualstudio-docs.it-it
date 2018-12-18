---
title: 'Idiaenumframedata:: Item | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d725c38073b82bc94081b3c27791e88f64343cd3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Recupera un elemento frame di dati tramite un indice.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 indice  
 [in] Indice del [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` restituito dal [idiaenumframedata:: Get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) metodo.  
  
 section  
 [out] Restituisce un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto che rappresenta l'elemento di dati di frame desiderato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)