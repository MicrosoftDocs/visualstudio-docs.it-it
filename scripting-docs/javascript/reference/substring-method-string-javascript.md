---
title: Metodo substring (String) (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="substring-method-string-javascript"></a>Metodo substring (String) (JavaScript)
Restituisce la sottostringa nella posizione specificata all'interno di un `String` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>Parametri  
 `start`  
 Obbligatorio. L'intero indice a base zero che indica l'inizio della sottostringa.  
  
 `end`  
 Parametro facoltativo. L'intero indice a base zero che indica la fine della sottostringa. La sottostringa include i caratteri fino a, ma non è incluso, il carattere indicato da `end`.  
  
 Se `end` viene omesso, i caratteri da `start` vengono restituiti fino alla fine della stringa originale.  
  
## <a name="remarks"></a>Note  
 Il `substring` metodo restituisce una stringa che contiene la sottostringa `start` backup, ma non include, `end`.  
  
 Il **sottostringa** viene utilizzato il valore minore di `start` e `end` come punto iniziale della sottostringa. Ad esempio, strvar.substring (0, 3**)** e strvar.substring (3, 0) restituiscono la stessa sottostringa.  
  
 Se il valore `start` o `end` è `NaN` o negativo, viene sostituito con zero.  
  
 La lunghezza della sottostringa è uguale al valore assoluto della differenza tra `start` e `end`. Ad esempio, la lunghezza della sottostringa restituita strvar.substring (0, 3) e strvar.substring (3, 0) è tre.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **sottostringa** metodo.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo substr (String)](../../javascript/reference/substr-method-string-javascript.md)