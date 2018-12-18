---
title: IDiaEnumSymbols::Clone | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c9f6eebf12ac9b51d617afca4abdedbba71af8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 ppenum  
 [out] Restituisce un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) oggetto che contiene un duplicato dell'enumeratore. I simboli non vengono duplicati, solo l'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)