---
title: Funzione Array. IsArray (JavaScript) | Documenti Microsoft
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
- isArray function [JavaScript]
- Array.isArray function [JavaScript]
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c31bdfe022cd41648117fc80c8df257e48e592ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="arrayisarray-function-javascript"></a>Funzione Array.isArray (JavaScript)
Determina se l'oggetto è una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Array.isArray(object)   
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto da testare.  
  
## <a name="return-value"></a>Valore restituito  
 `true` se `object` è una matrice, altrimenti `false`. Se l'argomento `object` non è un oggetto, viene restituito `false`.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Array.isArray`.  
  
```JavaScript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)   
 [Operatore typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)