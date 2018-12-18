---
title: Funzione isNaN (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isnan-function-javascript"></a>Funzione isNaN (JavaScript)
Restituisce un valore booleano che indica se un valore è il valore riservato `NaN` (non un numero).  
  
## <a name="syntax"></a>Sintassi  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>Valore restituito  
 `true` se il valore convertito nel tipo `Number` è `NaN` in caso contrario, `false`.  
  
## <a name="remarks"></a>Note  
 Obbligatorio `numValue` è il valore da confrontare `NaN`.  
  
 In genere, si usa questo metodo per testare i valori restituiti dai metodi `parseInt` e `parseFloat`.  
  
 In alternativa, una variabile che contiene `NaN` o un altro valore è analogo a se stesso. Se il confronto come diverso, è `NaN`. In questo modo `NaN` è l'unico valore che non è uguale a se stesso.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione isFinite](../../javascript/reference/isfinite-function-javascript.md)   
 [Costante NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Funzione parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Funzione parseInt](../../javascript/reference/parseint-function-javascript.md)