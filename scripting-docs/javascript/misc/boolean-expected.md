---
title: Previsto Boolean | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>Previsto Boolean
Si è tentato di richiamare il **Boolean.prototype.toString** o **Boolean.prototype.valueOf** su un oggetto di un tipo diverso da `Boolean`. L'oggetto di questo tipo di chiamata deve essere di tipo `Boolean`. Ad esempio:  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Valore booleano di richiamare solo**. prototype.toString** o **Boolean.prototype.valueOf** metodi su oggetti di tipo **booleano.**  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)   
 [Riepilogo dei tipi di dati](../../javascript/data-types-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Copia, passaggio e confronto di dati](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)