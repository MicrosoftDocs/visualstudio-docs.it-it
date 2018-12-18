---
title: 'Idiaenumsourcefiles:: Item | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1fda746edf51771e7927efd03094f42903141e6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Recupera un file di origine tramite un indice.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 indice  
 [in] Indice del [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) oggetto da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` restituito dal [idiaenumsourcefiles:: Get_count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) metodo.  
  
 sourceFile  
 [out] Restituisce un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) oggetto che rappresenta il file di origine desiderato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)