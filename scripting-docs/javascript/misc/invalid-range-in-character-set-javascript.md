---
title: Intervallo non valido nel carattere set (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d0d5ddf282c6994c572668136e6d7283794f6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervallo non valido nel set di caratteri (JavaScript)
Si è tentato di creare un'espressione regolare con un intervallo di set di caratteri non validi. Set di caratteri devono essere compreso tra singoli caratteri, ad esempio a-z o 0-9. è possibile includere le classi di caratteri, ad esempio \w in un set di caratteri. Il primo carattere dell'intervallo deve provenire anche prima del secondo carattere nell'intervallo. Ad esempio:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Utilizzare solo singoli caratteri di composizione del set di caratteri di espressione regolare e assicurarsi che siano disposti nell'ordine corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)