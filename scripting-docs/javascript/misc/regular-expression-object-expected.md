---
title: Previsto oggetto di espressione regolare | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a5a0f3cb3b86e2e01d522f85d0dae23e9c9d3ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-expected"></a>Previsto un oggetto di espressione regolare
Si è tentato di richiamare il **RegExp.prototype.toString** o **RegExp.prototype.valueOf** su un oggetto di un tipo diverso da `RegExp`. L'oggetto di questo tipo di chiamata deve essere di tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare solo il **RegExp.prototype.toString** o **RegExp.prototype.valueOf** metodi su oggetti di tipo `RegExp`.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)