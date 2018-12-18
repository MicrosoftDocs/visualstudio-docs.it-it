---
title: 'Idiaenumlinenumbers:: Next | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6015658a72c264f1421c782a1e6e6c28038748a1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Recupera un numero specificato di numeri di riga nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di numeri di riga nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Restituisce una matrice di [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) gli oggetti che rappresentano i numeri di riga desiderato.  
  
 pceltFetched  
 [out] Restituisce il numero di numeri di riga nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se sono non presenti più numeri di riga. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)