---
title: Metodo Map (Array) (JavaScript) | Documenti Microsoft
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
- map method [JavaScript]
- arrays [JavaScript], map method
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 609d9c88000a7a30fe8edc03b52df032f7d19ba9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="map-method-array-javascript"></a>Metodo map (Array) (JavaScript)
Chiama la funzione di callback specificata in ogni elemento di una matrice e restituisce una matrice contenente i risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. Oggetto matrice.|  
|`callbackfn`|Obbligatorio. Funzione che accetta fino a tre argomenti. Il metodo `map` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`thisArg`|Parametro facoltativo. Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`. Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## <a name="return-value"></a>Valore restituito  
 Nuova matrice in cui ogni elemento rappresenta il valore restituito della funzione di callback per l'elemento della matrice originale associato.  
  
## <a name="exceptions"></a>Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## <a name="remarks"></a>Note  
 Il metodo `map` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice, in ordine di indice crescente. La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `map` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
## <a name="callback-function-syntax"></a>Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, array1)`  
  
 È possibile dichiarare la funzione di callback usando un massimo di tre parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Argomento di callback|Definizione|  
|-----------------------|----------------|  
|`value`|Valore dell'elemento di matrice.|  
|`index`|Indice numerico dell'elemento di matrice.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## <a name="modifying-the-array-object"></a>Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `map`.  
  
|Condizione dopo l'avvio del metodo `map`|Elemento passato alla funzione di callback?|  
|---------------------------------------------|------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `map`.  
  
```JavaScript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  
  
```JavaScript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente un metodo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] incorporato viene utilizzato come funzione di callback.  
  
```JavaScript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## <a name="example"></a>Esempio  
 Il metodo `map` può essere applicato a una stringa. Questa condizione è illustrata nell'esempio seguente.  
  
```JavaScript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)   
 [Metodo Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Metodo forEach (Array)](../../javascript/reference/foreach-method-array-javascript.md)   
 [App di esempio JavaScript HiLo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)