---
title: Funzione Math.max (JavaScript) | Documenti Microsoft
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
- max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathmax-function-javascript"></a>Funzione Math.max (JavaScript)
Restituisce il più grande di un set di espressioni numeriche specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>Note  
 Facoltativo `number1, number2, ..., numberN` gli argomenti sono espressioni numeriche da valutare.  
  
 Se non sono forniti argomenti, il valore restituito è uguale a [Number.NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Se un argomento è `NaN`, anche il valore restituito è `NaN`.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come ottenere il più elevato tra due espressioni.  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Math.min](../../javascript/reference/math-min-function-javascript.md)