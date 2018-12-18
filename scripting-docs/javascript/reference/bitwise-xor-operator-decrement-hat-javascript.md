---
title: Operatore XOR bit per bit (^) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, XOR operator
- XOR operator
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebe8ff9805793bf306688622b0b29007b1562e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-operator--javascript"></a>Operatore XOR bit per bit (^) (JavaScript)
Esegue un'operazione di OR esclusivo bit per bit su due espressioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 ^ expression2  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Il  **^**  confrontata la rappresentazione binaria dei valori di due espressioni ed eseguita un'operazione di OR esclusiva bit per bit su di essi. Il risultato di questa operazione si comporta come segue:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Quando una sola delle espressioni è 1 in una cifra, il risultato è 1 in tale cifra. In caso contrario, il risultato è 0 in tale cifra.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore di assegnazione XOR bit per bit (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)