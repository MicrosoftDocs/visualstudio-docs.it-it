---
title: Metodo slice (Array) (JavaScript) | Documenti Microsoft
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>Metodo slice (Array) (JavaScript)
Restituisce una sezione di una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto `Array`.  
  
 `start`  
 Obbligatorio. Inizio della parte specificata di `arrayObj`.  
  
 `end`  
 Parametro facoltativo. La fine della parte specificata di `arrayObj`.  
  
## <a name="remarks"></a>Note  
 Il `slice` metodo restituisce un `Array` contenente la parte specificata dell'oggetto `arrayObj`.  
  
 Il `slice` metodo copia fino all'elemento indicato da escluso `end`. Se `start` è negativo, viene considerato come `length`  +  `start`, dove `length` è la lunghezza della matrice. Se `end` è negativo, viene considerato come `length`  +  `end` dove `length` è la lunghezza della matrice. Se `end` viene omesso, l'estrazione continua fino alla fine di `arrayObj`. Se `end` si verifica prima `start`, nessun elemento verrà copiato nella nuova matrice.  
  
## <a name="example"></a>Esempio  
 Gli esempi seguenti mostrano come usare il metodo `slice`. Nel primo esempio, tutte tranne l'ultimo elemento di `myArray` viene copiato in `newArray`. Nel secondo esempio, solo gli ultimi due elementi di `myArray` vengono copiati in `newArray`.  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo slice (String)](../../javascript/reference/slice-method-string-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)