---
title: Istruzione continue (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="continue-statement-javascript"></a>Istruzione continue (JavaScript)
Interrompe l'iterazione corrente di un ciclo e avvia una nuova iterazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>Note  
 Facoltativo `label` argomento specifica l'istruzione in cui `continue` si applica.  
  
 È possibile utilizzare il `continue` istruzione solo all'interno un `while`, `do...while`, **per**, o `for...in` ciclo. L'esecuzione di `continue` istruzione interrompe l'iterazione corrente del ciclo e continua il flusso di programma con l'inizio del ciclo. Questo comporta gli effetti seguenti sui diversi tipi di cicli:  
  
-   `while`e `do...while` cicli verifica della condizione e se è true, viene rieseguito il ciclo.  
  
-   `for`cicli eseguita l'espressione di incremento e se è true, l'espressione di test viene rieseguito il ciclo.  
  
-   `for...in`cicli nel campo successivo della variabile specificata e rieseguito il ciclo.  
  
## <a name="examples"></a>Esempi  
 In questo esempio, un ciclo viene ripetuto da 1 a 9. Le istruzioni comprese tra `continue` e la fine del `for` corpo vengono ignorate a causa dell'utilizzo del `continue` istruzione con l'espressione `(i < 5)`.  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 Nel codice seguente, il `continue` istruzione fa riferimento al `for` ciclo che è preceduto dal `Inner:` etichetta. Quando `j` è 24, il `continue` fa in modo che `for` ciclo all'iterazione successiva. I numeri compresi tra 21 e 23 e 25 e 30 stampa su ogni riga.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione Do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [for.... nell'istruzione](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled (istruzione)](../../javascript/reference/labeled-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)