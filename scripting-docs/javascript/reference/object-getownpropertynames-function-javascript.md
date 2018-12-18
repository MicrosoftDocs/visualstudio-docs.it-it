---
title: Funzione Object. getownpropertynames (JavaScript) | Documenti Microsoft
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertynames-function-javascript"></a>Funzione Object.getOwnPropertyNames (JavaScript)
Restituisce i nomi delle proprietà personalizzate di un oggetto. La proprietà di un oggetto sono quelle che sono definiti direttamente sull'oggetto e non vengono ereditate dal prototipo dell'oggetto. Le proprietà di un oggetto includono i campi (oggetti) e funzioni.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`object`|Obbligatorio. Oggetto che contiene le proprietà personalizzate.|  
  
## <a name="return-value"></a>Valore restituito  
 Matrice che contiene i nomi delle proprietà personalizzate dell'oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 Se il valore fornito per il `object` argomento non è il nome di un oggetto, un `TypeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
 Il `getOwnPropertyNames` metodo restituisce i nomi di metodi e proprietà enumerabili e non è enumerabile. Per restituire solo i nomi dei metodi e proprietà enumerabile, è possibile utilizzare il [funzione Object. Keys](../../javascript/reference/object-keys-function-javascript.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente crea un oggetto che presenta tre proprietà e un metodo. Viene quindi utilizzato il `getOwnPropertyNames` per ottenere le proprietà personalizzate (incluso il metodo) dell'oggetto.  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra i nomi delle proprietà che iniziano con la lettera ' in un **spaghetti** oggetto costruito con la **Pasta** costruttore.  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object.keys](../../javascript/reference/object-keys-function-javascript.md)