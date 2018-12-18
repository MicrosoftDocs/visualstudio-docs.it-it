---
title: Operatore di assegnazione AND bit per bit (&amp;=) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>Operatore di assegnazione AND bit per bit (&amp;=) (JavaScript)
Imposta il risultato di un'operazione con AND bit per bit sul valore di una variabile e il valore di un'espressione. La variabile e l'espressione vengono trattati come interi a 32 bit.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression`  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Utilizzando questo operatore è lo stesso effetto:  
  
```JavaScript  
result = result & expression  
```  
  
 Il [operatore AND bit per bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) esamina la rappresentazione binaria dei valori di `result` e `expression` ed eseguita un'operazione AND bit per bit su di essi. L'output di questa operazione si comporta come segue:  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 Qualsiasi tempo di che entrambe le espressioni sono 1 in cifre, il risultato è 1 in tale cifra. In caso contrario, il risultato è 0 in tale cifra.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore AND bit per bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)