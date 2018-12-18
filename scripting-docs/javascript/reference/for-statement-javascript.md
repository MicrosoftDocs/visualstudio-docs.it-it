---
title: Istruzione for (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="for-statement-javascript"></a>Istruzione for (JavaScript)
Esegue un blocco di istruzioni purché una determinata condizione è true.  
  
## <a name="syntax"></a>Sintassi  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>Parametri  
 `initialization`  
 Parametro facoltativo. Un'espressione. Questa espressione viene eseguita una sola volta, prima che venga eseguito il ciclo.  
  
 `test`  
 Parametro facoltativo. Espressione booleana. Se `test` è `true`, `statement` viene eseguita. Se `test` se `false`, il ciclo viene interrotto.  
  
 `increment`  
 Parametro facoltativo. Un'espressione. L'espressione di incremento viene eseguita alla fine di ogni iterazione del ciclo.  
  
 `statement`  
 Parametro facoltativo. Una o più istruzioni da eseguire se `test` è **true**. Può essere un'istruzione composta.  
  
## <a name="remarks"></a>Note  
 In genere utilizzato un `for` ciclo quando il ciclo è per essere eseguito un numero limitato di volte. Oggetto `for` ciclo è utile per scorrere le matrici e per eseguire elaborazione sequenziale.  
  
 Il test di un'espressione condizionale avviene prima dell'esecuzione del ciclo, pertanto un `for` istruzione viene eseguito zero o più volte.  
  
 In qualsiasi riga in un `for` blocco di istruzione di ciclo, è possibile utilizzare il `break` uscire dal ciclo oppure è possibile utilizzare il `continue` istruzione per trasferire il controllo all'iterazione successiva del ciclo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il `for` istruzione esegue le istruzioni incluse nel modo seguente:  
  
-   Innanzitutto, il valore iniziale della variabile `i` viene valutata.  
  
-   Quindi, purché il valore di `i` è minore o uguale a 9, il `document.write` le istruzioni vengono eseguite e `i` viene rivalutata.  
  
-   Quando `i` è maggiore di 9, la condizione non diventa false e il controllo viene trasferito all'esterno del ciclo.  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>Esempio  
 Tutte le espressioni del `for` istruzione sono facoltativi. Nell'esempio seguente, il `for` istruzioni consentono di creare un ciclo infinito e un `break` istruzione viene utilizzata per uscire dal ciclo.  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [for.... nell'istruzione](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)