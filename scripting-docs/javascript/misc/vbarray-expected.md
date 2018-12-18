---
title: Previsto VBArray | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-expected"></a>Previsto VBArray
È stato fornito un oggetto che non era un safeArray di Visual Basic, previsto.  
  
```  
new VBArray(safeArray);  
```  
  
 Gli oggetti VBArray sono di sola lettura e non possono essere creati direttamente. L'argomento di safeArray è un valore VBArray e deve aver ottenuto un valore VBArray prima di essere passati al `VBArray` costruttore. Ciò può essere ottenuto solo recuperando il valore da un oggetto ActiveX o altro esistente.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Assicurarsi passare solo **VBArray** oggetti per il **VBArray** costruttore.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)