---
title: Funzione Object. Seal (JavaScript) | Documenti Microsoft
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectseal-function-javascript"></a>Funzione Object.seal (JavaScript)
Impedisce la modifica degli attributi di proprietà esistenti, e impedisce l'aggiunta di nuove proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto su cui si desidera bloccare gli attributi.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto che viene passato alla funzione.  
  
## <a name="exceptions"></a>Eccezioni  
 Se il `object` argomento non è un oggetto, un `TypeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
 Il `Object.seal` funzione esegue entrambe le operazioni seguenti:  
  
-   Rende l'oggetto non estendibile, in modo che non è possibile aggiungervi nuove proprietà.  
  
-   Imposta il `configurable` attributo `false` per tutte le proprietà dell'oggetto.  
  
 Quando il `configurable` attributo `false`, non è possibile modificare gli attributi delle proprietà e la proprietà non può essere eliminata. Quando `configurable` è `false` e `writable` è `true`, `value` e `writable` gli attributi possono essere modificati.  
  
 Il `Object.seal` funzione non modifica il `writable` attributo.  
  
 Per ulteriori informazioni su come impostare gli attributi delle proprietà, vedere [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Per ottenere gli attributi di una proprietà, è possibile utilizzare il [funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
 Le seguenti funzioni correlate impediscono la modifica degli attributi dell'oggetto.  
  
|Funzione|Oggetto è reso non estendibile|`configurable`è impostato su `false` per ogni proprietà|`writable`è impostato su `false` per ogni proprietà|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sì|No|No|  
|`Object.seal`|Sì|Sì|No|  
|[Object. Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sì|Sì|Sì|  
  
 Le seguenti funzioni restituiscono `true` se vengono soddisfatte tutte le condizioni nella tabella seguente.  
  
|Funzione|Oggetto è estensibile?|`configurable`è `false` per tutte le proprietà?|`writable`è `false` per tutte le proprietà di dati?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sì|No|No|  
|[Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|No|  
|[Object. IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Object.seal`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Funzione Object. Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Funzione Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)