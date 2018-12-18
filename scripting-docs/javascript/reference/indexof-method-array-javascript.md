---
title: Metodo indexOf (Array) (JavaScript) | Documenti Microsoft
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
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-array-javascript"></a>Metodo indexOf (Array) (JavaScript)
Restituisce l'indice della prima occorrenza di un valore in una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. Oggetto matrice.|  
|`searchElement`|Obbligatorio. Valore da individuare `array1`.|  
|`fromIndex`|Parametro facoltativo. Indice della matrice in corrispondenza del quale iniziare la ricerca. Se `fromIndex` viene omesso, la ricerca inizia in corrispondenza dell'indice 0.|  
  
## <a name="return-value"></a>Valore restituito  
 L'indice della prima occorrenza di `searchElement` nella matrice oppure -1 se `searchElement` non viene trovato.  
  
## <a name="remarks"></a>Note  
 Il `indexOf` Cerca in una matrice per un valore specificato. Il metodo restituisce l'indice della prima occorrenza, oppure -1 se non viene trovato il valore specificato.  
  
 Viene eseguita la ricerca in ordine di indice crescente.  
  
 Gli elementi della matrice vengono confrontati con il `searchElement` valore di uguaglianza strict, simile al `===` operatore. Per ulteriori informazioni, vedere [gli operatori di confronto](../../javascript/reference/comparison-operators-javascript.md).  
  
 Facoltativo `fromIndex` argomento specifica l'indice di matrice in corrispondenza del quale iniziare la ricerca. Se `fromIndex` è maggiore o uguale alla lunghezza della matrice, viene restituito -1. Se `fromIndex` è negativo, la ricerca ha inizio la lunghezza della matrice più `fromIndex`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `indexOf` metodo.  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)