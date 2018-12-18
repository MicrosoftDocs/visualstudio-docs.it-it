---
title: Costanti Math (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="math-constants-javascript"></a>Costanti Math (JavaScript)
Math (costanti) restituiscono valori costanti che sono proprietà del `Math` oggetto.  
  
## <a name="math-object-constants"></a>Costanti matematiche dell'oggetto  
 Nella tabella seguente sono elencati i valori costanti che sono proprietà del [Math (oggetto)](../../javascript/reference/math-object-javascript.md).  
  
|Costante|Descrizione|Valore approssimativo|  
|--------------|-----------------|-----------------------|  
|`Math.E`|Costante matematica e. Rappresenta il numero di Eulero, ovvero la base dei logaritmi naturali.|2.718|  
|`Math.LN2`|Logaritmo naturale di 2.|0.693|  
|`Math.LN10`|Logaritmo naturale di 10.|2.302|  
|`Math.LOG2E`|Logaritmo in base 2 di e.|1.443|  
|`Math.LOG10E`|Logaritmo in base 10 di e.|0.434|  
|`Math.PI`|Pi greco. Rappresenta il rapporto tra la circonferenza di un cerchio e il suo diametro.|3.14159|  
|`Math.SQRT1_2`|Radice quadrata di 0,5 oppure uno diviso per la radice quadrata di 2.|0.707|  
|`Math.SQRT2`|Radice quadrata di 2.|1.414|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `Math.PI` costante.  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Math (oggetto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti numeriche](../../javascript/reference/number-constants-javascript.md)   
 [Costanti JavaScript](../../javascript/reference/javascript-constants.md)