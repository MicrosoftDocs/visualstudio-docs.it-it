---
title: Previsto &#39;] &#39; Nell'espressione regolare (JavaScript) | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Previsto &#39;] &#39; Nell'espressione regolare (JavaScript)
Tentativo di creare una classe di caratteri per trovare una corrispondenza di espressione regolare, ma non include la parentesi quadra chiusa. Combinazioni di caratteri letterali singoli possono essere assemblate in classi di caratteri, inserirli all'interno delle parentesi quadre. Una classe di caratteri corrisponde a qualsiasi carattere che contiene. Ad esempio / [abc] / corrisponde a uno qualsiasi dei caratteri "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere le parentesi all'espressione regolare.  
  
    > [!NOTE]
    >  Se si desidera corrisponde una parentesi singola, utilizzare caratteri di escape con una barra rovesciata - \\[, in modo che non viene interpretato come un carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)