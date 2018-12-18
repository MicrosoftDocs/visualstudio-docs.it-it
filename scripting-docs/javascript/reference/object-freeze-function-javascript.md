---
title: Funzione Object. Freeze (JavaScript) | Documenti Microsoft
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectfreeze-function-javascript"></a>Funzione Object.freeze (JavaScript)
Impedisce la modifica degli attributi e dei valori di proprietà esistenti, e impedisce l'aggiunta di nuove proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto su cui si desidera bloccare gli attributi.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto che viene passato alla funzione.  
  
## <a name="exceptions"></a>Eccezioni  
 Se il `object` argomento non è un oggetto, un `TypeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
 Il `Object.freeze` funzione esegue le operazioni seguenti:  
  
-   Rende l'oggetto non estendibile, in modo che non è possibile aggiungervi nuove proprietà.  
  
-   Imposta il `configurable` attributo `false` per tutte le proprietà dell'oggetto. Quando `configurable` è `false`, gli attributi della proprietà non possono essere modificati e la proprietà non può essere eliminata.  
  
-   Imposta il `writable` attributo `false` per tutte le proprietà di dati dell'oggetto. Quando `writable` è false, il valore della proprietà dati non può essere modificato.  
  
 Per ulteriori informazioni su come impostare gli attributi delle proprietà, vedere [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Per ottenere gli attributi di una proprietà, è possibile utilizzare il [funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
 Le seguenti funzioni correlate impediscono la modifica degli attributi dell'oggetto.  
  
|Funzione|Oggetto è reso non estendibile|`configurable`è impostato su `false` per ogni proprietà|`writable`è impostato su `false` per ogni proprietà|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sì|No|No|  
|[Object. Seal](../../javascript/reference/object-seal-function-javascript.md)|Sì|Sì|No|  
|`Object.freeze`|Sì|Sì|Sì|  
  
 Le seguenti funzioni restituiscono `true` se vengono soddisfatte tutte le condizioni nella tabella seguente.  
  
|Funzione|Oggetto è estensibile?|`configurable`è `false` per tutte le proprietà?|`writable`è `false` per tutte le proprietà di dati?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sì|No|No|  
|[Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|Sì|  
|[Object. IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Object.freeze`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Funzione Object. Seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Funzione Object. isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Funzione Object. IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)