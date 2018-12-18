---
title: Metodo Replace (String) (JavaScript) | Documenti Microsoft
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
- replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82894a5d7f92c8231a6ba3a1948369fb2c819a6d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="replace-method-string-javascript"></a>Metodo replace (String) (JavaScript)
Sostituisce il testo in una stringa usando un'espressione regolare o una stringa di ricerca.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringObj.replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto `String` o valore letterale stringa in cui eseguire la sostituzione. Questa stringa non è stata modificata dal **sostituire** metodo. ma il valore restituito da questo metodo è la stringa prodotta dalla sostituzione.  
  
 `rgExp`  
 Obbligatorio. Un'istanza di un **espressione regolare** oggetto contenente il criterio di espressione regolare e i flag applicabili. Può essere anche un oggetto `String` o un valore letterale stringa che rappresenta l'espressione regolare. Se `rgExp` non è un'istanza di un **espressione regolare** oggetto, viene convertito in una stringa e viene eseguita una ricerca esatta dei risultati, viene eseguito alcun tentativo di convertire la stringa in un'espressione regolare.  
  
 `replaceText`  
 Obbligatorio. Oggetto `String` o valore letterale stringa contenente il testo con cui sostituire tutte le corrispondenze di `rgExp` individuate in `stringObj`. In [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive l'argomento `replaceText` può essere anche una funzione che restituisce il testo di sostituzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il risultato del **sostituire** metodo è una copia di `stringObj` dopo avere apportate le sostituzioni specificate.  
  
## <a name="remarks"></a>Note  
 Ognuna delle seguenti variabili di corrispondenza può essere utilizzata per identificare la corrispondenza più recente e la stringa da cui proviene. Le variabili di corrispondenza possono essere utilizzate nella sostituzione del testo laddove la stringa in cui eseguire la sostituzione deve essere determinata dinamicamente.  
  
|Caratteri|Significato|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive)|  
|**$&**|Specifica la parte di `stringObj` corrispondente all'intero criterio di ricerca ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive)|  
|`$``|Specifica la parte di `stringObj` che precede la corrispondenza descritta da  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive)|  
|`$'`|Specifica la parte di `stringObj` che segue la corrispondenza descritta da  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive)|  
|`$`  ***n***|Il  *n* esima sottocorrispondenza acquisita, dove  *n*  è una singola cifra decimale compreso tra 1 e 9. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive)|  
|`$`  ***nn***|Il  *nn* esima sottocorrispondenza acquisita, dove  *nn*  è un numero decimale a due cifre compreso tra 01 e 99. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive)|  
  
 Se `replaceText` è una funzione, per ciascuna sottostringa corrispondente la funzione viene chiamata con il codice seguente *m* + 3 argomenti in cui *m* è il numero delle parentesi di acquisizione nel `rgExp`. Il primo argomento è la sottostringa corrispondente. Alla successiva *m* argomenti sono tutte le catture risultanti dalla ricerca. Argomento *m* + 2 è l'offset all'interno di `stringObj` in cui si è verificata la corrispondenza e l'argomento *m* + 3 è `stringObj`. Il risultato è un valore stringa derivante dalla sostituzione di ogni sottostringa trovata con il valore corrispondente restituito della chiamata di funzione.  
  
 Il **sostituire** metodo aggiorna le proprietà dell'oggetto globale `RegExp` oggetto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **sostituire** metodo per sostituire tutte le istanze di "the" con "a".  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Inoltre, il **sostituire** metodo può anche sostituire sottoespressioni nei criteri. L'esempio seguente scambia ogni coppia di parole nella stringa.  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumped lazy the dog.  
```  
  
 L'esempio seguente, compatibile con [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] e versioni successive, illustra come usare una funzione che restituisce il testo di sostituzione. Sostituisce qualsiasi istanza di un numero seguito da "F" con un valore convertito in Celsius.  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Metodo Match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)   
 [Metodo Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Metodo test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmazione di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternanza e sottoespressioni (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreference (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 trascinare e rilasciare l'app di esempio](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)