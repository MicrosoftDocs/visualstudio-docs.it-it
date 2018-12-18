---
title: Funzione Object. isextensible (JavaScript) | Documenti Microsoft
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
- Object.isExtensible function [JavaScript]
- isExtensible function [JavaScript]
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f88a61917811a5c6b5583e6c30539efc682296df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectisextensible-function-javascript"></a>Funzione Object.isExtensible (JavaScript)
Restituisce un valore che indica se possono essere aggiunte nuove proprietà a un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
Object.isExtensible(object)  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto da testare.  
  
## <a name="return-value"></a>Valore restituito  
 `true`Se l'oggetto è estensibile, che indica che è possibile aggiungere nuove proprietà all'oggetto. in caso contrario, `false`.  
  
## <a name="exceptions"></a>Eccezioni  
 Se il `object` argomento non è un oggetto, un `TypeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
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
|`Object.isExtensible`|Sì|No|No|  
|[Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|No|  
|[Object. IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Object.isExtensible`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Funzione Object. Seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Funzione Object. Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)