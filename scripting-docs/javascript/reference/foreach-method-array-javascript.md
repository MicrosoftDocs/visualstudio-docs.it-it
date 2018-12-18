---
title: Metodo forEach (Array) (JavaScript) | Documenti Microsoft
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
- forEach method [JavaScript]
- arrays [JavaScript], forEach method
- callback function, forEach method [JavaScript]
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec35c49e272ba50e26d3e4e7d892aa719a090d73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-array-javascript"></a>Metodo forEach (Array) (JavaScript)
Esegue l'azione specificata per ogni elemento in una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. Oggetto matrice.|  
|`callbackfn`|Obbligatorio. Funzione che accetta fino a tre argomenti. `forEach` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`thisArg`|Parametro facoltativo. Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`. Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## <a name="exceptions"></a>Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## <a name="remarks"></a>Note  
 Il metodo `forEach` chiama la funzione `callbackfn` una volta per ogni elemento presente nella matrice, in ordine di indice crescente. La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `forEach` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
## <a name="callback-function-syntax"></a>Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, array1)`  
  
 È possibile dichiarare la funzione di callback usando un massimo di tre parametri.  
  
 I parametri della funzione di callback sono i seguenti.  
  
|Argomento di callback|Definizione|  
|-----------------------|----------------|  
|`value`|Valore dell'elemento di matrice.|  
|`index`|Indice numerico dell'elemento di matrice.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## <a name="modifying-the-array-object"></a>Modifica dell'oggetto matrice  
 Il metodo `forEach` non modifica direttamente la matrice originale, mentre la funzione di callback può modificarla. Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `forEach`.  
  
|Condizione dopo l'avvio del metodo `forEach`|Elemento passato alla funzione di callback?|  
|---------------------------------------------|------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `forEach`.  
  
```JavaScript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, l'argomento `callbackfn` include il codice della funzione di callback.  
  
```JavaScript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  
  
```JavaScript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Metodo Map (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [Metodo Some (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)   
 [App di esempio JavaScript HiLo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)