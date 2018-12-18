---
title: "Non è possibile assegnare a un risultato di funzione | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-a-function-result"></a>Assegnazione a un risultato di funzione non consentita
Si è tentato di assegnare un valore a un risultato di funzione. Il risultato di una funzione può essere assegnato a una variabile, ma non può essere utilizzato come una variabile. Se si desidera assegnare un nuovo valore alla funzione stessa, omettere le parentesi (operatore di chiamata di funzione). L'esempio seguente illustra una situazione in cui viene generato l'errore.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Non utilizzare il valore di risultato di una chiamata di funzione come un elemento è possibile *assegnare*. È possibile assegnare il risultato della chiamata di funzione *a una variabile* se.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   In alternativa, è possibile assegnare la funzione stessa (e non il relativo valore restituito) a una variabile.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Scrittura di codice JavaScript](../../javascript/writing-javascript-code.md)   
 [Funzioni](../../javascript/functions-javascript.md)