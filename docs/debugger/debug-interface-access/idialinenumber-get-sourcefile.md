---
title: IDiaLineNumber::get_sourceFile | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFile method
ms.assetid: 86fc4411-375e-4b99-8f96-4da2c3f68190
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8833d1a5ccc39cac70cef6995a4e9a5c1bf99125
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialinenumbergetsourcefile"></a>IDiaLineNumber::get_sourceFile
Recupera un riferimento al file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_sourceFile (   
   IDiaSourceFile** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) oggetto che rappresenta il file di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)