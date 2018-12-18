---
title: Previsto oggetto | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6add25325653627d23eb699ab53c0f2799c8322f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="object-expected"></a>Previsto oggetto
Si è tentato di richiamare un metodo o una proprietà in un oggetto di tipo diverso da `Object` oppure è stato passato un argomento di tipo diverso da `Object` quando era obbligatorio un `Object`.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare il metodo o la proprietà solo in oggetti di tipo `Object`.  
  
-   Se l'errore si verifica per un argomento non oggetto, passare un oggetto di tipo `Object`.  
  
-   Verificare se viene richiamato un riferimento non definito o Null invece di un oggetto di tipo `Object`.  
  
     Ad esempio, se si verifica questo errore su myVar nel codice seguente:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     È possibile usare invece questo codice:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Object](../../javascript/reference/object-object-javascript.md)   
 [Oggetti e matrici](../../javascript/objects-and-arrays-javascript.md)