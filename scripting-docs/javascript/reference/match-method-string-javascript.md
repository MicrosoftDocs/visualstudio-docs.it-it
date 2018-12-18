---
title: Metodo Match (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>Metodo match (String) (JavaScript)
Corrisponde a una stringa con un'espressione regolare e restituisce una matrice contenente i risultati della ricerca.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Il `String` o valore letterale stringa in cui eseguire la ricerca.  
  
 `rgExp`  
 Obbligatorio. Un oggetto di espressione regolare che contiene il criterio di espressione regolare e i flag applicabili. Questo può anche essere un nome di variabile o un valore letterale stringa contenente il criterio di espressione regolare e i flag.  
  
## <a name="remarks"></a>Note  
 Se il `match` metodo non viene trovata una corrispondenza, restituito `null`. Se viene trovata una corrispondenza, `match` restituisce una matrice e le proprietà dell'oggetto globale `RegExp` oggetto vengono aggiornati per riflettere i risultati della corrispondenza.  
  
 Se il flag globale (`g`) non è impostata, elemento zero della matrice contiene l'intera corrispondenza, mentre gli elementi da 1 a  *n*  conterranno le sottocorrispondenze. Questo comportamento è lo stesso come il comportamento del [metodo exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md) quando il flag globale non è impostato. Se il flag globale è impostata, gli elementi da 0 a  *n*  includono tutte le corrispondenze che si sono verificati.  
  
 Se il flag globale non è impostata, la matrice restituita dal `match` metodo ha due proprietà, `input` e `index`. Il `input` proprietà contiene l'intera stringa cercata. Il `index` proprietà contiene la posizione della sottostringa corrispondente all'interno dell'intera stringa cercata.  
  
 Se il flag `i` è impostata, la ricerca non è tra maiuscole e minuscole.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `match`.  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)   
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Metodo Replace (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [Metodo Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Metodo test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmazione di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternanza e sottoespressioni (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreference (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)