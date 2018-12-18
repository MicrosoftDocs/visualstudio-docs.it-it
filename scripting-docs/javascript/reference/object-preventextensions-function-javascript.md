---
title: Funzione Object. preventextensions (JavaScript) | Documenti Microsoft
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
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectpreventextensions-function-javascript"></a>Funzione Object.preventExtensions (JavaScript)
Impedisce l'aggiunta di nuove proprietà a un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. L'oggetto è reso non estendibile.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto che viene passato alla funzione.  
  
## <a name="exceptions"></a>Eccezioni  
 Se il `object` argomento non è un oggetto, un `TypeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
 Il `Object.preventExtensions` funzione rende un oggetto non estensibile, in modo che non è possibile aggiungervi nuove proprietà denominate. Dopo che un oggetto viene reso non estendibile, non può essere resa estendibile.  
  
 Per informazioni su come impostare gli attributi delle proprietà, vedere [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
 Le seguenti funzioni correlate impediscono la modifica degli attributi dell'oggetto.  
  
|Funzione|Oggetto è reso non estendibile|`configurable`è impostato su `false` per ogni proprietà|`writable`è impostato su `false` per ogni proprietà|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|Sì|No|No|  
|[Object. Seal](../../javascript/reference/object-seal-function-javascript.md)|Sì|Sì|No|  
|[Object. Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sì|Sì|Sì|  
  
 Le seguenti funzioni restituiscono `true` se vengono soddisfatte tutte le condizioni nella tabella seguente.  
  
|Funzione|Oggetto è estensibile?|`configurable`è `false` per tutte le proprietà?|`writable`è `false` per tutte le proprietà di dati?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sì|No|No|  
|[Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|No|  
|[Object. IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Object.preventExtensions`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object. Seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Funzione Object. Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Funzione Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)