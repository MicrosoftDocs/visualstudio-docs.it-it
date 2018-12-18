---
title: IDiaLoadCallback2::RestrictDBGAccess | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b75db393822dc6c5d65bbbab4c9ccc64eed9f630
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Determina se cercando le informazioni di debug da file DBG.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT RestrictDBGAccess();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Diverso da qualsiasi valore restituito `S_OK` per impedire cercando le informazioni di debug da file DBG.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)