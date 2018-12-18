---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd3cd1f4989e88c41039328cdc4d54071ff49bac
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina se è possibile cercare un file con estensione pdb nella directory di debug originale.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Diverso da qualsiasi codice restituito `S_OK` impedisce la ricerca di un file con estensione pdb nella directory di debug originale. La directory di debug è il percorso del file di simboli compilato l'eseguibile quando si attiva il debug. Questo percorso non è necessariamente lo stesso come il percorso in cui è presente il file eseguibile.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)