---
title: 'Idiaenumsegments:: Next | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc61b94fb3443282c774719e21f7f7f072858bb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Recupera un numero di segmenti nella sequenza di enumerazione specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di segmenti nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Matrice che deve essere compilato con l'oggetto desiderato [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) gli oggetti che rappresentano i segmenti.  
  
 pceltFetched  
 [out] Restituisce il numero di segmenti nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se sono presenti non sono presenti più segmenti. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)