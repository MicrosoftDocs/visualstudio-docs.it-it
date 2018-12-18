---
title: IDiaLineNumber::get_columnNumberEnd | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3d7dd317cf24f2580d72fdc05ccbb8f60668fd1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Recupera il numero di colonna di origine basato su uno in cui termina l'espressione o istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di colonna in cui termina l'espressione o istruzione. Se il valore è zero, le informazioni di fine della colonna non sono presente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore della colonna restituito da questo metodo è un offset nella riga per la posizione dopo l'ultimo carattere dell'istruzione nella riga di byte.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)