---
title: Funzione Math. Acos (JavaScript) | Documenti Microsoft
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
- acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Funzione Math.acos (JavaScript)
Restituisce l'arcocoseno (o coseno inverso) di un numero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>Parametri  
 L'argomento `number` obbligatorio è un'espressione numerica.  
  
## <a name="return-value"></a>Valore restituito  
 L'arcocoseno del `number` argomento, in radianti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come usare la funzione `acos`.  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>Note  
 **Si applica a**: [Math (oggetto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Math. asin](../../javascript/reference/math-asin-function-javascript.md)   
 [Funzione Math. Atan](../../javascript/reference/math-atan-function-javascript.md)   
 [Funzione Math.cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Funzione Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Funzione Math.Tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Oggetto Math](../../javascript/reference/math-object-javascript.md)