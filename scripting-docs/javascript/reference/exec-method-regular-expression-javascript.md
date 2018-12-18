---
title: Metodo exec (Regular Expression) (JavaScript) | Documenti Microsoft
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
- exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="exec-method-regular-expression-javascript"></a>Metodo exec (Regular Expression) (JavaScript)
Esegue una ricerca in una stringa utilizzando un modello di espressione regolare e restituisce una matrice contenente i risultati della ricerca.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>Parametri  
 `rgExp`  
 Obbligatorio. Un'istanza di un **espressione regolare** oggetto contenente il criterio di espressione regolare e i flag applicabili.  
  
 `str`  
 Obbligatorio. Il `String` o valore letterale stringa in cui eseguire la ricerca.  
  
## <a name="remarks"></a>Note  
 Se il `exec` metodo non viene trovata una corrispondenza, restituito `null`. Se viene trovata una corrispondenza, `exec` restituisce una matrice e le proprietà dell'oggetto globale `RegExp` oggetto vengono aggiornati per riflettere i risultati della corrispondenza. Elemento zero della matrice contiene l'intera corrispondenza, mentre gli elementi da 1 -  *n*  conterranno le sottocorrispondenze che si sono verificati all'interno della corrispondenza. Questo comportamento è identico a quello del `match` metodo senza il flag globale (**g**) impostato.  
  
 Se il flag globale è impostato per un'espressione regolare, `exec` inizio in corrispondenza della posizione indicata dal valore di stringa di ricerca `lastIndex`. Se il flag globale non è impostato, `exec` ignora il valore di `lastIndex` e ricerche dall'inizio della stringa.  
  
 La matrice restituita dal `exec` metodo ha tre proprietà, **input**, **indice** e **lastIndex.** Il **input** proprietà contiene l'intera stringa cercata. Il **indice** proprietà contiene la posizione della sottostringa corrispondente all'interno dell'intera stringa cercata. Il `lastIndex` proprietà contiene la posizione dopo l'ultimo carattere nella corrispondenza.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `exec` metodo:  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Metodo Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Metodo test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmazione di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)