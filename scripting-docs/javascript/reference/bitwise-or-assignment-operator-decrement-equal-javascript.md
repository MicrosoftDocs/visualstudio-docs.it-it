---
title: Bit per bit operatore di assegnazione OR (| =) (JavaScript) | Documenti Microsoft
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
- '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>Operatore di assegnazione OR bit per bit (|=) (JavaScript)
Esegue un'operazione OR bit per bit sul valore di una variabile e il valore di un'espressione e assegna il risultato alla variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *espressione*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Utilizzando questo operatore è esattamente lo stesso effetto:  
  
```JavaScript  
result = result | expression  
```  
  
 Il **&#124; =** operatore esamina la rappresentazione binaria dei valori di *risultato* e *espressione* ed eseguita un'operazione OR bit per bit su di essi. Il risultato di questa operazione si comporta come segue:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Ogni volta che una delle espressioni con valore 1 nella stessa posizione, il risultato è 1 in tale cifra. In caso contrario, il risultato è 0 in tale cifra.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [OR bit per bit (operatore) (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)