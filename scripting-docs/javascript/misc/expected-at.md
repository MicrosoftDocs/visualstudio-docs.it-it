---
title: Previsto &#39; @&#39; | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f007129aa8da3ac49112fbc83b7abd31e4356c4f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939"></a>Previsto &#39; @&#39;
Si è tentato di creare una variabile da utilizzare con istruzioni di compilazione condizionale utilizzando il `@set` istruzione, ma non è stato inserito un simbolo di chiocciola "**@**" prima del nome della variabile.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere un simbolo di chiocciola "**@**" immediatamente prima il nome della variabile. Ad esempio:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [@setIstruzione](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)