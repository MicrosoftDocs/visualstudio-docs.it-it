---
title: IDiaLoadCallback2::RestrictSystemRootAccess | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 000d0b5ce21b6b50b1abab76aa8bf4a7bb1cd62a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Determina se la ricerca di file con estensione PDB è consentita nella directory radice di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Diverso da qualsiasi codice restituito `S_OK` impedisce la ricerca di directory di sistema per i file con estensione pdb.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)