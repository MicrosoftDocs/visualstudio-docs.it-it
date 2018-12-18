---
title: Questa istruzione (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="this-statement-javascript"></a>Istruzione this (JavaScript)
Fa riferimento all'oggetto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
this.property  
```  
  
## <a name="remarks"></a>Note  
 L'argomento obbligatorio `property` è una delle proprietà correnti dell'oggetto  
  
 La parola chiave `this` viene utilizzata nei costruttori di oggetti per fare riferimento all'oggetto corrente.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, **questo** fa riferimento al nuovo oggetto Car e assegna valori a tre proprietà:  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 Il **questo** (parola chiave) si intende in genere il **finestra** se utilizzata all'esterno dell'ambito di qualsiasi altro oggetto. Tuttavia, nei gestori eventi `this` fa riferimento all'elemento DOM che ha generato l'evento.  
  
 Nel codice seguente (per Internet Explorer 9 e versioni successive), il gestore eventi visualizza la versione della stringa di un pulsante con un ID "clicker".  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Uso del metodo bind](../../javascript/advanced/using-the-bind-method-javascript.md)