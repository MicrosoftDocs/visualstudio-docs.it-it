---
title: Funzione Math.min (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Funzione Math.min (JavaScript)
Restituisce il più piccolo di un set di espressioni numeriche.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>Note  
 Facoltativo `number1, number2, ..., numberN` gli argomenti sono espressioni numeriche da valutare.  
  
 Se non sono forniti argomenti, il valore restituito è uguale a [POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Se un argomento è `NaN`, anche il valore restituito è `NaN`.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come ottenere il più piccolo tra due espressioni.  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Math.max](../../javascript/reference/math-max-function-javascript.md)