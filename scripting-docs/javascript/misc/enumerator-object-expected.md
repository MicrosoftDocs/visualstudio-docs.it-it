---
title: Previsto oggetto Enumerator | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06005f635e5173e903cfba6a952750d64181d0bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946342"
---
# <a name="enumerator-object-expected"></a>Previsto oggetto Enumerator
Si è provato a richiamare il **metodo Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** oppure **Enumerator.prototype.moveNext** metodo in un oggetto di un tipo diverso rispetto a `Enumerator`. L'oggetto di questo tipo di chiamata deve essere di tipo `Enumerator`. Ecco un esempio di codice che causa l'interruzione di questa regola:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo le **metodo Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, o  **Enumerator.prototype.moveNext** metodi su oggetti di tipo `Enumerator`. Per determinare se l'oggetto è un `Enumerator` oggetto, usare:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)