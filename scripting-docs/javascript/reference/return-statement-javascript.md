---
title: Istruzione return (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="return-statement-javascript"></a>Istruzione return (JavaScript)
Esce dalla funzione corrente e restituisce un valore da tale funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>Note  
 Facoltativo *espressione* argomento è il valore da restituire dalla funzione. Se omesso, la funzione non restituisce un valore.  
  
 Utilizzare il `return` istruzione per arrestare l'esecuzione di una funzione e restituire il valore di *espressione*. Se *espressione* viene omesso o non `return` istruzione viene eseguita da all'interno della funzione, l'espressione che ha chiamato la funzione corrente viene assegnato il valore undefined.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `return`.  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `return` istruzione per restituire una funzione.  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)