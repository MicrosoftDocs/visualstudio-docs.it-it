---
title: Funzione Object. defineproperties (JavaScript) | Documenti Microsoft
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
helpviewer_keywords:
- Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Funzione Object.defineProperties (JavaScript)
Aggiunge una o più proprietà a un oggetto e/o modifica gli attributi di una proprietà esistente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto su cui si desidera aggiungere o modificare le proprietà. Può essere nativo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto o un oggetto DOM.  
  
 `descriptors`  
 Obbligatorio. Oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto che contiene uno o più oggetti descrittore. Ogni oggetto descrittore descrive una proprietà di dati o una proprietà di accesso.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto che è stato passato alla funzione.  
  
## <a name="remarks"></a>Note  
 Il `descriptors` argomento è un oggetto che contiene uno o più oggetti descrittore.  
  
 Oggetto *proprietà dati* è una proprietà che è possibile archiviare e recuperare un valore. Un descrittore di proprietà di dati contiene un `value` attributo, un `writable` attributo o entrambi. Per ulteriori informazioni, vedere [proprietà dei dati e le proprietà della funzione di accesso](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Un *proprietà di accesso* chiama una funzione fornito dall'utente ogni volta che il valore della proprietà è impostato o recuperato. Un descrittore di proprietà della funzione di accesso contiene un `set` attributo, un `get` attributo o entrambi.  
  
 Se l'oggetto dispone già di una proprietà con il nome specificato, vengono modificati gli attributi della proprietà. Per ulteriori informazioni, vedere [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Per creare un oggetto e aggiungere proprietà al nuovo oggetto, è possibile utilizzare il [funzione Object. create](../../javascript/reference/object-create-function-javascript.md).  
  
## <a name="adding-properties"></a>Aggiunta di proprietà  
 Nell'esempio seguente, il `Object.defineProperties` funzione aggiunge una proprietà di dati e una proprietà di accesso a un oggetto definito dall'utente.  
  
 L'esempio Usa un valore letterale di oggetto per creare il `descriptors` dell'oggetto con il `newDataProperty` e `newAccessorProperty` oggetti descrittore.  
  
```JavaScript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Come illustrato nell'esempio precedente, l'esempio seguente aggiunge le proprietà in modo dinamico anziché con un valore letterale di oggetto.  
  
```JavaScript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## <a name="modifying-properties"></a>Modifica delle proprietà  
 Per modificare gli attributi delle proprietà per l'oggetto, aggiungere il codice seguente. Il `Object.defineProperties` funzione modifica il `writable` attributo di `newDataProperty`e la modifica di `enumerable` attributo di `newAccessorProperty`. Aggiunge `anotherDataProperty` per l'oggetto perché tale nome di proprietà non esiste già.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>Requisiti  
 Supportato in standard di Internet Explorer 9, standard di Internet Explorer 10, e [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] app. Supportato in Internet Explorer 8 DOM solo per gli oggetti, in caso contrario non è supportato.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Funzione Object. getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Funzione Object. create](../../javascript/reference/object-create-function-javascript.md)   
 [Oggetto Object](../../javascript/reference/object-object-javascript.md)