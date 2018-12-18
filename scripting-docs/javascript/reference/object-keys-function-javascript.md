---
title: Funzione Object. Keys (JavaScript) | Documenti Microsoft
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectkeys-function-javascript"></a>Funzione Object.keys (JavaScript)
Restituisce i nomi delle proprietà e dei metodi enumerabili di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`object`|Obbligatorio. Oggetto che contiene le proprietà e metodi. Può trattarsi di un oggetto che è stato creato o un oggetto esistente di Strumentazione gestione Windows (DOM, Document Object Model).|  
  
## <a name="return-value"></a>Valore restituito  
 Matrice che contiene i nomi delle proprietà enumerabili e i metodi dell'oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 Se il valore fornito per il `object` argomento non è il nome di un oggetto, un `TypeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
 Il `keys` restituisce solo i nomi dei metodi e le proprietà enumerabili. Per restituire i nomi di metodi e proprietà enumerabili e non è enumerabile, è possibile utilizzare [funzione Object. getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Per informazioni di `enumerable` attributo di una proprietà, vedere [funzione Object. DefineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) e [funzione Object. getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente crea un oggetto che presenta tre proprietà e un metodo. Viene quindi utilizzato il `keys` metodo per ottenere le proprietà e metodi dell'oggetto.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono visualizzati i nomi di tutte le proprietà enumerabili che iniziano con la lettera "g" nell'oggetto Pasta.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)