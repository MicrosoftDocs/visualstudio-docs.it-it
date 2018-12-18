---
title: Previsto &#39;) &#39; Nell'espressione regolare (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Previsto &#39;) &#39; Nell'espressione regolare (JavaScript)
Tentativo di creare un gruppo, l'asserzione o l'acquisizione di espressioni regolari, ma non include la parentesi di chiusura. Tra parentesi hanno scopi diversi nelle espressioni regolari. In primo luogo, vengono usati per acquisire le sottoespressioni, per specificare le asserzioni, o per raggruppare modelli in modo che gli elementi possono essere considerati come una singola unità dal *, +,? e così via.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere le parentesi di chiusura a destra.  
  
    > [!NOTE]
    >  Se si desidera corrisponde una parentesi singola, utilizzare caratteri di escape con una barra rovesciata - \\(- in modo che non viene interpretato come un carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)