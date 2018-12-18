---
title: IDiaLoadCallback::RestrictSymbolServerAccess | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0860741429599630f99c5e2c7c538eff08ecda2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Determina se l'accesso viene consentito a un server di simboli per risolvere i simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Diverso da qualsiasi codice restituito `S_OK` impedisce l'uso di un server di simboli per risolvere i simboli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)