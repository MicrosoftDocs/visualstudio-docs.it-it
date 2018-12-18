---
title: '&#39; restituito &#39; istruzione all''esterno della funzione | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="39return39-statement-outside-of-function"></a>&#39; restituito &#39; istruzione all'esterno della funzione
È stato utilizzato un `return` istruzione nell'ambito globale del codice. Il `return` istruzione deve essere visualizzato solo all'interno del corpo di una funzione.  
  
 Richiamo di una funzione con il `()` operatore è un'espressione. Tutte le espressioni sono valori. il `return` istruzione viene utilizzata per specificare il valore restituito da una funzione. Il formato generale è:  
  
```  
  
return [ expression ];  
```  
  
 Quando il `return` viene eseguita l'istruzione, *espressione* viene valutato e restituito come valore della funzione. Se è presente alcuna espressione, **definito** viene restituito.  
  
 Esecuzione della funzione si interrompe quando il `return` istruzione viene eseguita, anche se sono presenti altre istruzioni ancora nel corpo della funzione. L'eccezione a questa regola è se il **restituire** istruzione si trova all'interno di un **provare** blocco, e non esiste un corrispondente **infine** blocco, il codice nel  **infine** blocco verrà eseguito prima del termine della funzione.  
  
 Se una funzione restituisce poiché non raggiunge la fine del corpo della funzione senza eseguire un `return` istruzione, il valore restituito è il **definito** valore (in questo caso il risultato della funzione non può essere utilizzato come parte di un'espressione più grande ).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Rimuovere il `return` istruzione dal corpo principale del codice (ambito globale).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione return](../../javascript/reference/return-statement-javascript.md)   
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Proprietà caller (Function)](../../javascript/reference/caller-property-function-javascript.md)