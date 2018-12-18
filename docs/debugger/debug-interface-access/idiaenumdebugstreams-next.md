---
title: 'Idiaenumdebugstreams:: Next | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 780aaca4d840d87df17572ec7d58cebc84e84d4c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
Recupera un numero specificato di flussi di debug nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Next (   
   ULONG                     celt,   
   IDiaEnumDebugStreamData** rgelt,  
   ULONG*                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] **T**ha numero di flussi di debug nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Restituisce una matrice di [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) gli oggetti che rappresentano il debug di flussi da recuperare.  
  
 pceltFetched  
 [out] Restituisce il numero di flussi debug restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se nessun flusso altre. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)