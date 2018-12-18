---
title: Oggetto reflect (JavaScript) | Documenti Microsoft
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="reflect-object-javascript"></a>Oggetto Reflect (JavaScript)
Fornisce i metodi da usare nelle operazioni intercettate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>Parametri  
 `method`  
 Obbligatorio. Nome di uno dei metodi dell'oggetto `Reflect`.  
  
## <a name="remarks"></a>Note  
 Non è possibile creare un'istanza dell'oggetto Reflect con l'operatore `new`.  
  
 Riflettere metodi vengono spesso usati con [proxy](../../javascript/reference/proxy-object-javascript.md) perché consentono di delegare al comportamento predefinito senza implementare il comportamento predefinito nel codice.  
  
 Reflect fornisce un metodo statico con lo stesso nome di ogni trap proxy. Le descrizioni nella tabella non sono esaurienti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Simile al [applicare](../../javascript/reference/apply-method-function-javascript.md) metodo dell'oggetto funzione.|  
|`Reflect.construct(target, args)`|Funzione equivalente all'operatore `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Simile a [Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Restituisce un valore booleano che indica se la chiamata è riuscita.|  
|`Reflect.deleteProperty(target, propertyName)`|Simile all'istruzione `delete`. Restituisce un valore booleano che indica se la chiamata è riuscita.|  
|`Reflect.enumerate(target)`|Simile a [for.... in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) istruzione [Object. getownpropertysymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object. Keys](../../javascript/reference/object-keys-function-javascript.md) funzione, e [JSON. stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Funzione equivalente per qualsiasi [getter](../../javascript/creating-objects-javascript.md) proprietà.|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Simile a [Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md). Restituisce un valore booleano che indica se la chiamata è riuscita.|  
|`Reflect.getPrototypeOf(target)`|Simile a [Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Simile al `in` operatore [metodo hasOwnProperty (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)e altri metodi. Restituisce un valore booleano che indica se la chiamata è riuscita.|  
|`Reflect.isExtensible(target)`|Simile a [Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Simile a [getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Simile a [Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md). Restituisce un valore booleano che indica se la chiamata è riuscita.|  
|`Reflect.set(target, propertyName, value, receiver)`|Simile all'uso di qualsiasi [setter](../../javascript/creating-objects-javascript.md) proprietà. Restituisce un valore booleano che indica se la chiamata è riuscita.|  
|`Reflect.setPrototypeOf(target, prototype)`|Simile a [setprototypeof](../../javascript/reference/object-setprototypeof-function-javascript.md). Restituisce un valore booleano che indica se la chiamata è riuscita.|  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come usare `Reflect.get` per scrivere un proxy che blocca le operazioni get per le proprietà che iniziano con un carattere di sottolineatura.  
  
```JavaScript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]