---
title: Previsto oggetto Enumerator | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485e6e387f07fd3a54727f5f8e08c0a00743c6d9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-expected"></a>Previsto oggetto Enumerator
Si è tentato di richiamare il **metodo Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** o **Enumerator.prototype.moveNext** su un oggetto di un tipo rispetto a `Enumerator`. L'oggetto di questo tipo di chiamata deve essere di tipo `Enumerator`. Di seguito è riportato un esempio di codice che viola questa regola:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare solo il **metodo Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, o  **Enumerator.prototype.moveNext** metodi su oggetti di tipo `Enumerator`. Per determinare se l'oggetto è un `Enumerator` oggetto, usare:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)