---
title: Previsto oggetto Date | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-expected"></a>Previsto oggetto date
Si è tentato di richiamare il **Date.prototype.toString** o **Date.prototype.valueOf** su un oggetto di un tipo diverso da `Date`. L'oggetto di questo tipo di chiamata deve essere di tipo `Date`. Ad esempio:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Richiamare solo il **Date.prototype.toString** o **Date.prototype.valueOf** metodi su oggetti di tipo `Date`.  
  
## <a name="see-also"></a>Vedere anche  
 [Date (oggetto)](../../javascript/reference/date-object-javascript.md)   
 [Metodo getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Oggetti intrinseci](../../javascript/intrinsic-objects-javascript.md)