---
title: IDiaStackWalkHelper::imageForVA | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0986a6a0b4596671cb11b40b938848387124462f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Restituisce l'inizio dell'immagine di un file eseguibile in memoria di un indirizzo virtuale in un punto nello spazio di memoria dell'eseguibile specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `vaContext`  
 [in] L'indirizzo virtuale che si trova in un punto nello spazio dell'eseguibile.  
  
 `pvaImageStart`  
 [out] Restituisce l'indirizzo virtuale iniziale dell'immagine dell'eseguibile.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)