---
title: Metodo test (Regular Expression) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="test-method-regular-expression-javascript"></a>Metodo test (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica se esiste o meno un modello in una stringa di ricerca.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>Parametri  
 `rgExp`  
 Obbligatorio. Un'istanza di un **espressione regolare** oggetto contenente il criterio di espressione regolare e i flag applicabili.  
  
 `str`  
 Obbligatorio. La stringa in cui eseguire la ricerca.  
  
## <a name="remarks"></a>Note  
 Il **test** metodo controlla se un modello esistente all'interno di una stringa e restituisce **true** in tal caso, e **false** in caso contrario.  
  
 Le proprietà dell'oggetto globale `RegExp` oggetto non vengono modificati dal **test** metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **test** metodo. Per usare questo esempio, passare la funzione di modello di espressione regolare e una stringa. La funzione verrà test per l'occorrenza del criterio di espressione regolare nella stringa e restituire una stringa che indica i risultati della ricerca:  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)   
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)