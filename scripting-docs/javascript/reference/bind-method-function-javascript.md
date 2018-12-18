---
title: Metodo Bind (Function) (JavaScript) | Documenti Microsoft
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
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bind-method-function-javascript"></a>Metodo bind (Function) (JavaScript)
Per una funzione specifica, crea una funzione associata che ha lo stesso corpo della funzione originale. Nella funzione associata l'oggetto `this` viene risolto nell'oggetto. La funzione associata contiene i parametri iniziali specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>Parametri  
 `function`  
 Obbligatorio. Oggetto funzione.  
  
 `thisArg`  
 Obbligatorio. Oggetto a cui la parola chiave `this` può fare riferimento nella nuova funzione.  
  
 `arg1`[,`arg2`[,`argN`]]]  
 Parametro facoltativo. Elenco di argomenti da passare alla nuova funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Nuova funzione uguale alla funzione `function`, ad eccezione dell'oggetto `thisArg` e degli argomenti iniziali.  
  
## <a name="exceptions"></a>Eccezioni  
 Se l'oggetto `function` specificato non è una funzione, viene generata un'eccezione `TypeError`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come utilizzare il metodo `bind`.  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'oggetto `thisArg` è diverso dall'oggetto che contiene il metodo originale.  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato come utilizzare gli argomenti `arg1[,arg2[,argN]]]`. La funzione associata utilizza i parametri specificati nel metodo `bind` come primo e secondo parametro. Tutti i parametri specificati quando la funzione associata viene chiamata vengono utilizzati come terzi parametri, quarti parametri e così via.  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Metodo Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Utilizzo del metodo bind](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [App di esempio JavaScript HiLo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)