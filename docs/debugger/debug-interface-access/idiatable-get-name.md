---
title: IDiaTable::get_name | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get_name method
ms.assetid: f6e9cd07-63cd-48a6-9835-e69c2d0859c5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dedf326d718c9d015aa488c1dc2fdf9210c4fc9e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiatablegetname"></a>IDiaTable::get_name
Recupera il nome della tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_name (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il nome della tabella.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)