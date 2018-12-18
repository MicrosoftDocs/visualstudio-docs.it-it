---
title: Funzione Object. Create (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectcreate-function-javascript"></a>Funzione Object.create (JavaScript)
Crea un oggetto che ha il prototipo specificato e che contiene facoltativamente le proprietà specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>Parametri  
 `prototype`  
 Obbligatorio. Oggetto da utilizzare come prototipo. Può essere `null`.  
  
 `descriptors`  
 Parametro facoltativo. Oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto che contiene uno o più descrittori di proprietà.  
  
 Un oggetto *proprietà dei dati* è una proprietà che può ottenere e impostare un valore. Un descrittore di proprietà di dati contiene un `value` attributo, oltre a `writable`, `enumerable`, e `configurable` gli attributi. Se non vengono specificati gli ultimi tre attributi, per impostazione predefinita per `false`. Un *proprietà di accesso* chiama una funzione fornito dall'utente ogni volta che il valore viene recuperato o impostato. Un descrittore di proprietà della funzione di accesso contiene un `set` attributo, un `get` attributo o entrambi. Per ulteriori informazioni, vedere [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="return-value"></a>Valore restituito  
 Nuovo oggetto che presenta il prototipo interno specificato e contiene le proprietà specificate, se presente.  
  
## <a name="exceptions"></a>Eccezioni  
 Oggetto `TypeError` eccezione viene generata in presenza delle condizioni seguenti:  
  
-   Il `prototype` argomento non è un oggetto e non è `null`.  
  
-   Un descrittore nel `descriptors` argomento abbia un `value` o `writable` e un `get` o `set` attributo.  
  
-   Un descrittore nel `descriptors` argomento abbia un `get` o `set` attributo che non è una funzione.  
  
## <a name="remarks"></a>Note  
 È possibile utilizzare questa funzione utilizzando un `null``prototype` parametro per interrompere la catena di prototipi. L'oggetto creato non sarà necessario alcun prototipo.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente crea un oggetto utilizzando un `null` prototipo e aggiunge due proprietà enumerabili.  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente crea un oggetto che ha lo stesso prototipo interno dell'oggetto all'oggetto. È possibile vedere che abbia lo stesso prototipo come un oggetto creato con un valore letterale di oggetto. Il [Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md) funzione Ottiene il prototipo dell'oggetto originale. Per ottenere il descrittore di proprietà dell'oggetto, è possibile utilizzare [funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente crea un oggetto che ha lo stesso prototipo interno dell'oggetto Shape.  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Metodo isPrototypeOf (Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Creazione di oggetti](../../javascript/creating-objects-javascript.md)