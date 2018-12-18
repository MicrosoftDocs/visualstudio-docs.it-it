---
title: Stringhe di modello (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="template-strings-javascript"></a>Stringhe di modello (JavaScript)
In [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] è possibile usare stringhe di modello per costruire valori letterali stringa con espressioni incorporate. Le stringhe di modello forniscono anche supporto integrato per stringhe a più righe.  
  
 Per costruire una stringa di modello, usare l'accento grave, chiamato anche apice inverso (`), per racchiudere la stringa, anziché le virgolette singole o doppie. L'esempio di codice seguente mostra una stringa di modello semplice.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Le stringhe di modello possono includere interruzioni di riga senza che sia necessario l'uso del carattere di avanzamento riga (\n).  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Il carattere $ viene usato per specificare segnaposto all'interno di una stringa di modello. La sintassi è ${*expression*}, dove *expression* è qualsiasi espressione JavaScript, ad esempio una variabile o una funzione, come illustrato nell'esempio seguente.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Funzioni di modello con tag, che permettono di modificare il valore di una stringa di modello usando una funzione richiamata con argomenti dalla stringa di modello. Il primo argomento è una matrice di valori letterali stringa, delimitata dalle espressioni della stringa di modello che contiene, mentre il secondo argomento è una matrice ([Rest parameter](../../javascript/functions-javascript.md)) che contiene i valori delle espressioni della stringa di modello.  
  
 Nell'esempio seguente viene usata la funzione di modello con tag buildURL per costruire un URL. La sintassi consiste nell'usare il nome della funzione seguito immediatamente dalla stringa di modello.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Se è necessario accedere ai valori stringa non elaborata passati, il primo argomento passato alla funzione di modello con tag supporta una proprietà `raw` che restituisce il formato stringa non elaborata delle stringhe passate.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  È anche possibile usare la funzione [String.raw](../../javascript/reference/string-raw-function-javascript.md) per restituire il formato stringa non elaborata di una stringa di modello.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento al linguaggio JavaScript](../../javascript/javascript-language-reference.md)   
 [JavaScript avanzato](../../javascript/advanced/advanced-javascript.md)