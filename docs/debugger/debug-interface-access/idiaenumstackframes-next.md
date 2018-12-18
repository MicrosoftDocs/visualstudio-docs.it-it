---
title: 'Idiaenumstackframes:: Next | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68e84c31cb98cdbbe69e62aa1e572386100277a0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Recupera un numero specificato di elementi di frame dello stack dalla sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di elementi stackframe nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Matrice che deve essere compilato con la richiesta [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) oggetti.  
  
 pceltFetched  
 [out] Restituisce il numero di stack di elementi frame nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se vi sono più stack frame. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)