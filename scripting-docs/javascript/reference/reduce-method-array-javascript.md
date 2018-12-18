---
title: Metodo reduce (Array) (JavaScript) | Documenti Microsoft
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
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76279f66f8e3180fdebd73b83eb31c7368cefc75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="reduce-method-array-javascript"></a>Metodo reduce (Array) (JavaScript)
Chiama la funzione di callback specificato per tutti gli elementi nella matrice. Il valore restituito della funzione di callback è il risultato accumulato e viene fornito come argomento nella chiamata successiva alla funzione di callback.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. Oggetto matrice.|  
|`callbackfn`|Obbligatorio. Una funzione che accetta fino a quattro argomenti. Il metodo `reduce` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`initialValue`|Parametro facoltativo. Se `initialValue` viene specificato, viene utilizzato come valore iniziale per avviare l'accumulo. La prima chiamata al `callbackfn` funzione questo valore viene fornito come argomento anziché un valore di matrice.|  
  
## <a name="return-value"></a>Valore restituito  
 Il risultato accumulato dall'ultima chiamata alla funzione di callback.  
  
## <a name="exceptions"></a>Eccezioni  
 Oggetto `TypeError` eccezione viene generata quando viene soddisfatta una delle condizioni seguenti:  
  
-   Il `callbackfn` argomento non è un oggetto funzione.  
  
-   La matrice non contiene elementi e `initialValue` non è stato specificato.  
  
## <a name="remarks"></a>Note  
 Se un `initialValue` viene fornito il `reduce` chiamate al metodo di `callbackfn` funzione una volta per ogni elemento presente nella matrice, in ordine di indice crescente. Se un `initialValue` non viene specificato, il `reduce` chiamate al metodo di `callbackfn` funzione su ogni elemento, a partire dal secondo elemento.  
  
 Il valore restituito della funzione di callback viene fornito come il `previousValue` argomento alla chiamata successiva alla funzione di callback. Il valore restituito dell'ultima chiamata alla funzione di callback è il valore restituito di `reduce` metodo.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
> [!NOTE]
>  Il [metodo reduceRight (Array)](../../javascript/reference/reduceright-method-array-javascript.md) elabora gli elementi in senso decrescente di indice.  
  
## <a name="callback-function-syntax"></a>Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a quattro parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Argomento di callback|Definizione|  
|-----------------------|----------------|  
|`previousValue`|Il valore dalla precedente chiamata alla funzione di callback. Se un `initialValue` viene fornito per il `reduce` (metodo), il `previousValue` è `initialValue` la prima volta che viene chiamata la funzione.|  
|`currentValue`|Il valore dell'elemento della matrice corrente.|  
|`currentIndex`|L'indice numerico dell'elemento della matrice corrente.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## <a name="first-call-to-the-callback-function"></a>Prima chiamata alla funzione di Callback  
 La prima volta che viene chiamata la funzione di callback, i valori forniti come argomenti dipendono il `reduce` metodo ha un `initialValue` argomento.  
  
 Se un `initialValue` viene fornito al metodo ridurre:  
  
-   Il valore dell'argomento `previousValue` è `initialValue`.  
  
-   Il `currentValue` argomento è il valore del primo elemento presente nella matrice.  
  
 Se un `initialValue` non è stato specificato:  
  
-   Il `previousValue` argomento è il valore del primo elemento presente nella matrice.  
  
-   Il `currentValue` argomento è il valore del secondo elemento presente nella matrice.  
  
## <a name="modifying-the-array-object"></a>Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `reduce`.  
  
|Condizione dopo l'avvio del metodo `reduce`|Elemento passato alla funzione di callback?|  
|------------------------------------------------|------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di concatenare i valori della matrice in una stringa, separare i valori con ":". Perché non è stato specificato alcun valore iniziale per il `reduce` (metodo), la prima chiamata alla funzione di callback è "abc" come il `previousValue` argomento e "def" come il `currentValue` argomento.  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente aggiunge i valori di una matrice dopo che sono stati arrotondati. Il `reduce` metodo viene chiamato con un valore iniziale pari a 0.  
  
```JavaScript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente aggiunge i valori in una matrice. Il `currentIndex` e `array1` i parametri vengono utilizzati nella funzione di callback.  
  
```JavaScript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente ottiene una matrice che contiene solo i valori sono compresi tra 1 e 10 in un'altra matrice. Il valore iniziale specificato per il `reduce` metodo è una matrice vuota.  
  
```JavaScript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo reduceRight (Array)](../../javascript/reference/reduceright-method-array-javascript.md)