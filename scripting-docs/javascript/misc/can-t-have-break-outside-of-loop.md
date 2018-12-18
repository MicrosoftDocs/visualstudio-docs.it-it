---
title: "Può &#39; dispone di t &#39; interruzione &#39; di fuori di ciclo | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Può &#39; dispone di t &#39; interruzione &#39; all'esterno del ciclo
Si è tentato di utilizzare il **interruzione** (parola chiave) di fuori di un ciclo. Il **interruzione** parola chiave viene utilizzata per terminare un ciclo o `switch` istruzione. Devono essere incorporato nel corpo di un ciclo o `switch` istruzione. Tuttavia, un **etichetta** possibile seguire la parola chiave break.  
  
```  
break labelname;  
```  
  
 È necessario solo la forma con etichetta del **interruzione** (parola chiave) quando si utilizzano i cicli annidati o `switch` istruzioni ed è necessario interrompere un ciclo che non è quello più interno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che il **interruzione** parola chiave viene visualizzata all'interno di un'istruzione di ciclo o switch.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Risoluzione dei problemi relativi agli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)