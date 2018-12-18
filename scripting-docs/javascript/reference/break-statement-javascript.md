---
title: Istruzione break (JavaScript) | Documenti Microsoft
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
- break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="break-statement-javascript"></a>Istruzione break (JavaScript)
Termina il ciclo corrente o se in combinazione con un `label`, termina l'istruzione associata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>Note  
 Facoltativo `label` argomento specifica l'etichetta dell'istruzione che viene interrotta.  
  
 In genere si usa il `break` istruzione `switch` istruzioni e in `while`, `for`, `for...in`, o `do...while` cicli. Viene in genere utilizzato il `label` argomento `switch` istruzioni, ma può essere utilizzato in qualsiasi istruzione, sia semplice o composta.  
  
 L'esecuzione di `break` istruzione viene chiusa dal ciclo corrente o istruzione e inizia l'esecuzione di script con l'istruzione immediatamente successiva.  
  
## <a name="examples"></a>Esempi  
 In questo esempio, il contatore è configurato per il conteggio da 1 a 99. Tuttavia, il `break` istruzione termina il ciclo dopo 14 conteggi.  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 Nel codice seguente, il `break` istruzione fa riferimento al `for` ciclo che è preceduto dal `Inner:` istruzione. Quando `j` è uguale a 24, il `break` fa in modo che il flusso di programma uscire dal ciclo. I numeri compresi tra 21 e 23 stampa su ogni riga.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)   
 [Istruzione Do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [for.... nell'istruzione](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled (istruzione)](../../javascript/reference/labeled-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)