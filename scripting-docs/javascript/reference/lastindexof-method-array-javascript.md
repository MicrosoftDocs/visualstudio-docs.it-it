---
title: Metodo lastIndexOf (Array) (JavaScript) | Documenti Microsoft
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
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>Metodo lastIndexOf (Array) (JavaScript)
Restituisce l'indice dell'ultima occorrenza di un valore specificato in una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. L'oggetto di matrice da cercare.|  
|`searchElement`|Obbligatorio. Valore da individuare `array1`.|  
|`fromIndex`|Parametro facoltativo. Indice della matrice in corrispondenza del quale iniziare la ricerca. Se `fromIndex` viene omesso, la ricerca inizia in corrispondenza dell'ultimo indice nella matrice.|  
  
## <a name="return-value"></a>Valore restituito  
 L'indice dell'ultima occorrenza di `searchElement` nella matrice oppure -1 se `searchElement` non viene trovato.  
  
## <a name="remarks"></a>Note  
 Il `lastIndexOf` Cerca in una matrice per un valore specificato. Il metodo restituisce l'indice della prima occorrenza, oppure -1 se non viene trovato il valore specificato.  
  
 Viene eseguita la ricerca nell'indice decrescente (ultimo membro prima). Per cercare in ordine crescente, usare il [metodo indexOf (Array)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Gli elementi della matrice vengono confrontati con il `searchElement` valore di uguaglianza strict, simile a quello effettuato dal `===` operatore. Per ulteriori informazioni, vedere [gli operatori di confronto](../../javascript/reference/comparison-operators-javascript.md).  
  
 Facoltativo `fromIndex` argomento specifica l'indice di matrice in corrispondenza del quale iniziare la ricerca. Se `fromIndex` è maggiore o uguale alla lunghezza della matrice, l'intera matrice viene eseguita la ricerca. Se `fromIndex` è negativo, la ricerca ha inizio la lunghezza della matrice più `fromIndex`. Se l'indice calcolata è minore di 0, viene restituito -1.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `lastIndexOf` metodo.  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo indexOf (Array)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)