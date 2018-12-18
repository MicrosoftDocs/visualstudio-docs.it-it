---
title: Quantificatore imprevisto (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="unexpected-quantifier-javascript"></a>Quantificatore imprevisto (JavaScript)
Quando si crea il criterio di ricerca di espressioni regolari, creato un elemento del modello con un fattore di ripetizioni non valido. Ad esempio, il criterio  
  
```  
/^+/  
```  
  
 non è valido perché l'elemento ^ (inizio dell'input) non può avere un fattore di ripetizioni. Nella tabella seguente sono elencati gli elementi che non possono avere i fattori di ripetizioni.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|^|Inizio dell'input|  
|$|Fine dell'input|  
|\b|Confine di parola|  
|\B|Confine di parola non|  
|*|Zero o più valori di ripetizione|  
|+|Uno o più valori di ripetizione|  
|?|Zero o più valori di ripetizione|  
|{n}|n ripetizioni|  
|{n}|n o altre ripetizioni|  
|{n, m}|Da n a m ripetizioni, inclusive|  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che l'elemento di criterio di ricerca contiene solo i fattori di ripetizioni legali.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)