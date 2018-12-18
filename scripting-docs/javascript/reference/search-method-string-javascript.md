---
title: Metodo Search (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="search-method-string-javascript"></a>Metodo search (String) (JavaScript)
Trova la prima corrispondenza della sottostringa in una ricerca di espressioni regolari.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Il `String` o valore letterale stringa in cui eseguire la ricerca.  
  
 `rgExp`  
 Obbligatorio. Un'istanza di un **espressione regolare** oggetto contenente il criterio di espressione regolare e i flag applicabili.  
  
## <a name="return-value"></a>Valore restituito  
 Se viene trovata una corrispondenza, il **ricerca** metodo restituisce un valore intero che indica l'offset dall'inizio della stringa in cui si è verificato durante la prima corrispondenza. Se viene trovata alcuna corrispondenza, viene restituito -1.  
  
## <a name="remarks"></a>Note  
 È inoltre possibile impostare il `i` flag che determina la ricerca ha tra maiuscole e minuscole.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **ricerca** metodo.  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Metodo Match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Metodo Replace (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [Metodo test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmazione di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)