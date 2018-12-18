---
title: Argomento replacer non valido | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 588909bae9c5cf198d3108490111b36d5a2d182b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="invalid-replacer-argument"></a>Argomento Replacer non valido
È stato effettuato un tentativo di richiamare `JSON.stringify` con un argomento che non è valido. Il `replacer` argomento deve essere una funzione o una matrice.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Modifica il `replacer` argomento in una funzione o una matrice.  
  
## <a name="example"></a>Esempio  
 Il codice in questo esempio provoca un errore di runtime perché `memberfilter` è un oggetto anziché una funzione o una matrice.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto JSON](../../javascript/reference/json-object-javascript.md)   
 [Funzione JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)