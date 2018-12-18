---
title: Compilazione condizionale disattivata | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-is-turned-off"></a>Compilazione condizionale disattivata
Si è tentato di utilizzare una variabile di compilazione condizionale senza prima compilazione condizionale di attivazione in. Attivazione della compilazione condizionale indica il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilatore a interpretare gli identificatori che iniziano con come variabili di compilazione condizionale. Questo scopo, a partire da codice con l'istruzione condizionale:  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere l'istruzione seguente all'inizio del codice condizionale:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onIstruzione](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@ifIstruzione](../../javascript/reference/at-if-statement-javascript.md)   
 [Istruzione @set](../../javascript/reference/at-set-statement-javascript.md)