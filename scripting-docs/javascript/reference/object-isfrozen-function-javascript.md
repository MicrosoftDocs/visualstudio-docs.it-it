---
title: Funzione Object. IsFrozen (JavaScript) | Documenti Microsoft
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
- isFrozen function [JavaScript]
- Object.isFrozen function [JavaScript]
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e1ccd11d5b4ef3b5f24dbfc8e815f0e3e156347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectisfrozen-function-javascript"></a>Funzione Object.isFrozen (JavaScript)
Restituisce `true` se gli attributi delle proprietà e i valori esistenti non possono essere modificati in un oggetto e non è possibile aggiungere nuove proprietà all'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
Object.isFrozen(object)  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto da testare.  
  
## <a name="return-value"></a>Valore restituito  
 `true`Se vengono soddisfatte tutte le operazioni seguenti:  
  
-   L'oggetto è non estendibile, che indica che non è possibile aggiungere nuove proprietà all'oggetto.  
  
-   Il `configurable` attributo `false` per tutte le proprietà esistenti.  
  
-   Il `writable` attributo `false` per tutte le proprietà di dati esistente.  
  
 Se l'oggetto non dispone di alcuna proprietà esistente, la funzione restituisce `true` se l'oggetto non estendibile.  
  
## <a name="exceptions"></a>Eccezioni  
 Se il `object` argomento non è un oggetto, un `TypeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
 Quando il `configurable` attributo di una proprietà è `false`, gli attributi della proprietà non possono essere modificati e la proprietà non può essere eliminata. Quando `writable` è `false`, il valore della proprietà dati non può essere modificato. Quando `configurable` è `false` e `writable` è `true`, `value` e `writable` gli attributi possono essere modificati.  
  
 Per informazioni su come impostare gli attributi delle proprietà, vedere [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Per ottenere gli attributi di una proprietà, è possibile utilizzare il [funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
 Le seguenti funzioni correlate impediscono la modifica degli attributi dell'oggetto.  
  
|Funzione|Oggetto è reso non estendibile|`configurable`è impostato su `false` per ogni proprietà|`writable`è impostato su `false` per ogni proprietà|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sì|No|No|  
|[Object. Seal](../../javascript/reference/object-seal-function-javascript.md)|Sì|Sì|No|  
|[Object. Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sì|Sì|Sì|  
  
 Le seguenti funzioni restituiscono `true` se vengono soddisfatte tutte le condizioni nella tabella seguente.  
  
|Funzione|Oggetto è estensibile?|`configurable`è `false` per tutte le proprietà?|`writable`è `false` per tutte le proprietà di dati?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sì|No|No|  
|[Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|No|  
|`Object.isFrozen`|No|Sì|Sì|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Object.isFrozen`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Funzione Object. Seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Funzione Object. Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Funzione Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)