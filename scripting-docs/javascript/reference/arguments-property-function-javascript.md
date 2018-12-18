---
title: "Proprietà Arguments (Function) (JavaScript) | Documenti Microsoft"
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
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-property-function-javascript"></a>Proprietà arguments (Function) (JavaScript)
Ottiene gli argomenti per l'esecuzione `Function` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>Note  
 Il `function` argomento è il nome della funzione attualmente in esecuzione e può essere omesso.  
  
 Questa proprietà consente di gestire un numero variabile di argomenti di una funzione. Il **lunghezza** proprietà del `arguments` oggetto contiene il numero di argomenti passati alla funzione. Ai singoli argomenti contenuti nel `arguments` può accedere all'oggetto nello stesso modo degli elementi di matrice.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'uso della proprietà `arguments`:  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto arguments](../../javascript/reference/arguments-object-javascript.md)   
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)