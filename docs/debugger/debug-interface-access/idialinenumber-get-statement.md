---
title: IDiaLineNumber::get_statement | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c259c7157ad98dee3830e96ca8922b88a2fe56c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
Recupera un flag che indica che le informazioni di riga vengono descritti l'inizio di un'istruzione, anziché un'espressione, in origine del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce `TRUE` se le informazioni di riga descrivono l'inizio di un'istruzione all'origine del programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le istruzioni possono estendersi su più righe. Questo metodo indica se il numero di riga associata contrassegna l'inizio di questo tipo di un'istruzione su più righe.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)