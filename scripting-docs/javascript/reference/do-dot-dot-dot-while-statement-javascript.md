---
title: Istruzione Do... (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>Istruzione do...while (JavaScript)
Esegue un blocco di istruzioni una volta e quindi ripete l'esecuzione del ciclo fino a che restituisce un'espressione della condizione `false`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>Parametri  
 `statement`  
 Obbligatorio. L'istruzione da eseguire se `expression` è `true`. Può essere un'istruzione composta.  
  
 `expression`  
 Obbligatorio. Un'espressione che può essere assegnata al valore booleano `true` o `false`. Se `expression` è `true`, il ciclo viene eseguito nuovamente. Se `expression` è `false`, il ciclo viene interrotto.  
  
## <a name="remarks"></a>Note  
 A differenza di `while` istruzione, una `do...while` ciclo viene eseguito una volta prima della valutazione dell'espressione condizionale.  
  
 In qualsiasi riga in un `do...while` blocco, è possibile utilizzare il `break` a causa del flusso di programma uscire dal ciclo oppure è possibile utilizzare il `continue` istruzione per passare direttamente al `while` espressione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, le istruzioni di `do...while` ciclo continua l'esecuzione fino a quando la variabile `i` è inferiore a 10.  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, le istruzioni all'interno del ciclo vengono eseguite una volta, anche se non viene soddisfatta la condizione.  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [for.... nell'istruzione](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while (istruzione)](../../javascript/reference/while-statement-javascript.md)   
 [Istruzione con etichetta](../../javascript/reference/labeled-statement-javascript.md)