---
title: Oggetto proxy (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ee75310f1d976e0a0896b1be34a80c594cdd054
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="proxy-object-javascript"></a>Oggetto Proxy (JavaScript)
Abilita il comportamento personalizzato per un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>Parametri  
 `target`  
 Obbligatorio. Oggetto o funzione che deve essere virtualizzato dal proxy.  
  
 `handler`  
 Obbligatorio. Oggetto contenente metodi (trap) che implementano il comportamento personalizzato.  
  
## <a name="remarks"></a>Note  
 Gli oggetti `Proxy` vengono usati per intercettare le operazioni di basso livello interne su un altro oggetto. Possono essere usati per l'intercettazione, la virtualizzazione di oggetti, la registrazione o il profiling e per altri scopi.  
  
 Se nel parametro handler del proxy non è stato definito un trap per un'operazione specifica, l'operazione viene inoltrata al parametro target.  
  
 L'oggetto handler definisce i metodi (trap) seguenti per implementare il comportamento personalizzato. Gli esempi seguenti non sono esaustivi. Per supportare il comportamento predefinito condizionale nel metodo del gestore, utilizzare i metodi di [riflettere oggetto](../../javascript/reference/reflect-object-javascript.md).  
  
|Sintassi del metodo (trap) di handler|Esempi di utilizzo|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|Trap per una chiamata di funzione.|  
|`construct: function(target, args)`|Trap per un costruttore.|  
|`defineProperty: function(target, propertyName, descriptor)`|Trap per [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Trap per l'istruzione `delete`.|  
|`enumerate: function(target)`|Trap per il [for.... in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) istruzione [Object. getownpropertysymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object. Keys](../../javascript/reference/object-keys-function-javascript.md) funzione, e [JSON. stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Trap per qualsiasi [getter](../../javascript/creating-objects-javascript.md) proprietà.|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Trap per [funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Trap per [funzione Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Trap per il `in` operatore [metodo hasOwnProperty (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)e altri metodi.|  
|`isExtensible: function(target)`|Trap per [funzione Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Trap per [funzione Object. getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Trap per [funzione Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Trap per qualsiasi [setter](../../javascript/creating-objects-javascript.md) proprietà.|  
|`setPrototypeOf: function(target, prototype)`|Trap per [setprototypeof](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come creare un proxy per un valore letterale dell'oggetto con il trap `get`.  
  
```JavaScript  
var target = {};  
var handler = {  
  get: function (target, property, receiver) {  
    // This example includes a template string.  
    return `Hello, ${property}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come creare un proxy per una funzione con il trap `apply`.  
  
```JavaScript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
