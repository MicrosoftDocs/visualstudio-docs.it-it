---
title: Numero di costanti (JavaScript) | Documenti Microsoft
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
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="number-constants-javascript"></a>Costanti Number (JavaScript)
Le seguenti costanti numeriche sono proprietà dell'oggetto `Number`.  
  
## <a name="number-object-constants"></a>Costanti numeriche oggetto  
 Per accedere a queste costanti non è necessario creare l'oggetto `Number`.  
  
|Costante|Valore restituito|  
|--------------|--------------------|  
|`Number.EPSILON`|Il numero più basso che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Equivale approssimativamente a 2.2204460492503130808472633361816E-16.|  
|`Number.MAX_SAFE_INTEGER`|Il numero più alto che può essere rappresentato in modo sicuro in JavaScript. È pari a 9007199254740991.|  
|`Number.MAX_VALUE`|Il numero più alto che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Equivale approssimativamente a 1.79E+308.|  
|`Number.MIN_SAFE_INTEGER`|Il numero più piccolo che può essere rappresentato in modo sicuro in JavaScript. Uguale a-9007199254740991.|  
|`Number.MIN_VALUE`|Il numero più vicino allo zero che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Equivale approssimativamente a 5.00E-324.|  
|`Number.NaN`|Un valore che non sia un numero.<br /><br /> Nei confronti di uguaglianza, `NaN` non equivale a nessun valore, incluso se stesso. Per verificare se il valore è equivalente a `NaN`, utilizzare il [funzione isNaN](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Un valore inferiore al numero negativo più alto che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mostra valori `NEGATIVE_INFINITY` come `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Un valore più alto del numero più alto che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mostra valori `POSITIVE_INFINITY` come `infinity`.|  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Per `Number.EPSILON`, `Number.MAX_SAFE_INTEGER`, e `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Si applica a**: [numero oggetto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Math (costanti)](../../javascript/reference/math-constants-javascript.md)   
 [Costanti JavaScript](../../javascript/reference/javascript-constants.md)   
 [Costante Infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [Costante NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Funzione isNaN](../../javascript/reference/isnan-function-javascript.md)