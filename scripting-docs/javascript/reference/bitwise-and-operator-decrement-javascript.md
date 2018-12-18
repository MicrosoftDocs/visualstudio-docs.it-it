---
title: Operatore AND bit per bit (&amp;) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '& operator, about & operator'
- AND operator
- '& operator'
- bitwise operators, AND operator
- '& operator, bitwise operators'
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b3eec0cbd7c172d08b16120fb54f3be3c6a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-operator-amp-javascript"></a>Operatore AND bit per bit (&amp;) (JavaScript)
Esegue un'operazione con AND bit per bit su due espressioni a 32 bit.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 & expression2  
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Risultato dell'operazione.  
  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Il `&` esegue un'operazione AND bit per bit su ciascuno dei bit di due espressioni a 32 bit. Se entrambi i bit sono 1, il risultato è 1. In caso contrario, il risultato è 0.  
  
|Bit1|Bit2|Valore individuato|  
|----------|----------|-----------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 Nell'esempio seguente viene illustrato come utilizzare il `&` operatore.  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore di assegnazione AND bit per bit (& =)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)