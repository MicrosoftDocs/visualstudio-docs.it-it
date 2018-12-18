---
title: Operatore Delete (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: delete_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- array elements, deleting
- properties, deleting
- delete operator
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee3def1977c0b29ee14ebf836f2d9ebb51d5a5ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="delete-operator-javascript"></a>Operatore delete (JavaScript)
Elimina una proprietà da un oggetto o rimuove un elemento da una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
delete expression  
```  
  
## <a name="remarks"></a>Note  
 Il `expression` argomento è un valido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] espressione comporta che, in genere un elemento di matrice o nome di proprietà.  
  
 Se il risultato di `expression` è un oggetto, la proprietà specificata `expression` esiste, e l'oggetto non consentiranno da eliminare, `false` viene restituito.  
  
 In tutti gli altri casi, `true` viene restituito.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come rimuovere un elemento da una matrice.  
  
```JavaScript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come eliminare le proprietà da un oggetto.  
  
```JavaScript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)