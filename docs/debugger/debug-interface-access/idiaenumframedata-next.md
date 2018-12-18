---
title: 'Idiaenumframedata:: Next | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6835cda6c8c2a5cb20135abf92a523a270b32c78
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Recupera un numero specificato di elementi frame di dati nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di elementi di dati di frame nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Matrice di [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetti per l'inserimento degli elementi di dati frame richiesto.  
  
 pceltFetched  
 [out] Restituisce il numero di elementi frame di dati nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti più record. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)