---
title: Metodo Every (Array) (JavaScript) | Documenti Microsoft
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="every-method-array-javascript"></a>Metodo every (Array) (JavaScript)
Determina se tutti i membri di una matrice soddisfano il test specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. Oggetto matrice.|  
|`callbackfn`|Obbligatorio. Funzione che accetta fino a tre argomenti. Il `every` chiamate al metodo di `callbackfn` funzione per ogni elemento in `array1` fino a quando il `callbackfn` restituisce `false`, o fino alla fine della matrice.|  
|`thisArg`|Parametro facoltativo. Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`. Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## <a name="return-value"></a>Valore restituito  
 `true`Se il `callbackfn` risultato della funzione `true` per tutte le matrici di elementi; in caso contrario, `false`. Se la matrice non contiene elementi, il `every` restituisce `true`.  
  
## <a name="exceptions"></a>Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## <a name="remarks"></a>Note  
 Il `every` chiamate al metodo di `callbackfn` funzione una volta per ogni elemento della matrice, nell'indice ordine crescente, finché il `callbackfn` risultato della funzione `false`. Se un elemento che causa `callbackfn` per restituire `false` viene trovato, il `every` metodo restituisce immediatamente `false`. In caso contrario, il `every` restituisce `true`.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `every` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
> [!NOTE]
>  È possibile utilizzare il [metodo some (Array)](../../javascript/reference/some-method-array-javascript.md) per verificare se la funzione di callback restituisce `true` per qualsiasi elemento della matrice.  
  
## <a name="callback-function-syntax"></a>Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, array1)`  
  
 È possibile dichiarare la funzione di callback con un massimo di tre parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Parametro di callback|Definizione|  
|------------------------|----------------|  
|`value`|Valore dell'elemento di matrice.|  
|`index`|Indice numerico dell'elemento di matrice.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## <a name="modifying-the-array-object"></a>Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `every`.  
  
|Condizione dopo l'avvio del metodo `every`|Elemento passato alla funzione di callback?|  
|-----------------------------------------------|------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `every`.  
  
```JavaScript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  
  
```JavaScript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Some (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Metodo Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)