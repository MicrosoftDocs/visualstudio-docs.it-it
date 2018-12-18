---
title: Operatore di assegnazione XOR bit per bit (^ =) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>Operatore di assegnazione XOR bit per bit (^=) (JavaScript)
Esegue un'operazione di OR esclusivo bit per bit su una variabile e un'espressione e assegna il risultato alla variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *espressione*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Utilizzo di  **^=**  operatore è lo stesso effetto:  
  
```JavaScript  
result = result ^ expression  
```  
  
 Il  **^=**  confrontata la rappresentazione binaria dei valori di due espressioni ed eseguita un'operazione di OR esclusiva bit per bit su di essi. Il risultato di questa operazione si comporta come segue:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Quando una sola delle espressioni è 1 in una cifra, il risultato è 1 in tale cifra. In caso contrario, il risultato è 0 in tale cifra.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore XOR bit per bit (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)