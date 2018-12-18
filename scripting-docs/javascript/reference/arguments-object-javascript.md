---
title: Oggetto arguments (JavaScript) | Documenti Microsoft
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-object-javascript"></a>Oggetto Arguments (JavaScript)
Oggetto che rappresenta gli argomenti della funzione attualmente in esecuzione e le funzioni che lo hanno chiamato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>Parametri  
 *function*  
 Parametro facoltativo. Il nome di attualmente in esecuzione `Function` oggetto.  
  
 *n*  
 Obbligatorio. L'indice in base zero per i valori di argomento passato al `Function` oggetto.  
  
## <a name="remarks"></a>Note  
 Non è possibile creare in modo esplicito un **argomenti** oggetto. Il **argomenti** oggetto diventa disponibile solo quando una funzione inizia l'esecuzione. Il **argomenti** oggetto della funzione non è una matrice, ma i singoli argomenti si accede esattamente gli elementi della matrice sono accessibili. L'indice  *n*  è effettivamente un riferimento a uno del **0**  ***n***  le proprietà del **argomenti** oggetto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **argomenti** oggetto.  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [0... n (proprietà) (argomenti)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [Proprietà callee (arguments)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [Proprietà length (arguments)](../../javascript/reference/length-property-arguments-javascript.md)