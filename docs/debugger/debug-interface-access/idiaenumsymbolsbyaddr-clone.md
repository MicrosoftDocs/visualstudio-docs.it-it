---
title: IDiaEnumSymbolsByAddr::Clone | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Clone method
ms.assetid: f4582c69-bc3f-4a26-bcca-b641102b85fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d60ad08c6ace9b0f130b0430e351689539480d97
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsymbolsbyaddrclone"></a>IDiaEnumSymbolsByAddr::Clone
Crea una copia di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Clone (   
   IDiaEnumSymbolsByAddr** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 ppenum  
 [out] Restituisce un [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) oggetto che contiene un duplicato dell'enumeratore. I simboli non vengono duplicati, solo l'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)