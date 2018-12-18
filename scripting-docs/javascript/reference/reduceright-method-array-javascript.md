---
title: Metodo reduceRight (Array) (JavaScript) | Documenti Microsoft
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="reduceright-method-array-javascript"></a>Metodo reduceRight (Array) (JavaScript)
Chiama la funzione di callback specificato per tutti gli elementi in una matrice, in ordine decrescente. Il valore restituito della funzione di callback è il risultato accumulato e viene fornito come argomento nella chiamata successiva alla funzione di callback.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. Oggetto matrice.|  
|`callbackfn`|Obbligatorio. Una funzione che accetta fino a quattro argomenti. Il metodo `reduceRight` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`initialValue`|Parametro facoltativo. Se `initialValue` viene specificato, viene utilizzato come valore iniziale per avviare l'accumulo. La prima chiamata al `callbackfn` funzione questo valore viene fornito come argomento anziché un valore di matrice.|  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto che contiene il risultato accumulato dall'ultima chiamata alla funzione di callback.  
  
## <a name="exceptions"></a>Eccezioni  
 Oggetto `TypeError` eccezione viene generata quando viene soddisfatta una delle condizioni seguenti:  
  
-   Il `callbackfn` argomento non è un oggetto funzione.  
  
-   La matrice non contiene elementi e `initialValue` non è stato specificato.  
  
## <a name="remarks"></a>Note  
 Se un `initialValue` viene fornito il `reduceRight` chiamate al metodo di `callbackfn` funzione una volta per ogni elemento della matrice, in senso decrescente di indice. Se non `initialValue` viene fornito il `reduceRight` chiamate al metodo di `callbackfn` funzione su ogni elemento, a partire dall'elemento secondo ultimo, in senso decrescente di indice.  
  
 Il valore restituito della funzione di callback viene fornito come il `previousValue` argomento alla chiamata successiva alla funzione di callback. Il valore restituito dell'ultima chiamata alla funzione di callback è il valore restituito di `reduceRight` metodo.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Per raccogliere un risultato in ordine di indice crescente, utilizzare il [metodo reduce (Array)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## <a name="callback-function-syntax"></a>Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a quattro parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Argomento di callback|Definizione|  
|-----------------------|----------------|  
|`previousValue`|Il valore dalla precedente chiamata alla funzione di callback. Se un `initialValue` viene fornito per il `reduceRight` (metodo), il `previousValue` è `initialValue` la prima volta che viene chiamata la funzione.|  
|`currentValue`|Il valore dell'elemento della matrice corrente.|  
|`currentIndex`|L'indice numerico dell'elemento della matrice corrente.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## <a name="first-call-to-the-callback-function"></a>Prima chiamata alla funzione di Callback  
 La prima volta che viene chiamata la funzione di callback, i valori forniti come argomenti dipendono il `reduceRight` metodo ha un `initialValue` argomento.  
  
 Se un `initialValue` viene fornito per il `reduceRight` metodo:  
  
-   Il valore dell'argomento `previousValue` è `initialValue`.  
  
-   Il `currentValue` argomento è il valore dell'ultimo elemento presente nella matrice.  
  
 Se un `initialValue` non è stato specificato:  
  
-   Il `previousValue` argomento è il valore dell'ultimo elemento presente nella matrice.  
  
-   Il `currentValue` argomento è il valore dell'elemento al penultimo presente nella matrice.  
  
## <a name="modifying-the-array-object"></a>Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `reduceRight`.  
  
|Condizione dopo l'avvio del metodo `reduceRight`|Elemento passato alla funzione di callback?|  
|-----------------------------------------------------|------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di concatenare i valori della matrice in una stringa, separare i valori con ":". Perché non è stato specificato alcun valore iniziale per il `reduceRight` metodo, la prima chiamata alla funzione di callback ha 456 come il `previousValue` argomento e 123 come il `currentValue` argomento.  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene calcolata la somma dei quadrati degli elementi della matrice. Il `reduceRight` metodo viene chiamato con un valore iniziale pari a 0.  
  
```JavaScript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente ottiene gli elementi di una matrice i cui valori sono compresi tra 1 e 10. Il valore iniziale specificato per il `reduceRight` metodo è una matrice vuota.  
  
```JavaScript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## <a name="example"></a>Esempio  
 Il metodo `reduceRight` può essere applicato a una stringa. Nell'esempio seguente viene illustrato come utilizzare questo metodo per invertire i caratteri in una stringa.  
  
```JavaScript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo reduce (Array)](../../javascript/reference/reduce-method-array-javascript.md)