---
title: Metodo Some (Array) (JavaScript) | Documenti Microsoft
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="some-method-array-javascript"></a>Metodo some (Array) (JavaScript)
Determina se la funzione di callback specificato restituisce `true` per qualsiasi elemento della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Definizione|  
|---------------|----------------|  
|`array1`|Obbligatorio. Oggetto matrice.|  
|`callbackfn`|Obbligatorio. Funzione che accetta fino a tre argomenti. Il `some` chiamate al metodo di `callbackfn` funzione per ogni elemento in `array1` fino a quando il `callbackfn` restituisce `true`, o fino alla fine della matrice.|  
|`thisArg`|Parametro facoltativo. Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`. Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## <a name="return-value"></a>Valore restituito  
 `true`Se il `callbackfn` risultato della funzione `true` per qualsiasi elemento della matrice; in caso contrario, `false`.  
  
## <a name="exceptions"></a>Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## <a name="remarks"></a>Note  
 Il `some` chiamate al metodo di `callbackfn` funzione su ogni elemento della matrice, nell'indice ordine crescente, finché il `callbackfn` risultato della funzione `true`. Se un elemento che causa `callbackfn` per restituire `true` viene trovato, il `some` metodo restituisce immediatamente `true`. Se non viene restituito il callback `true` su qualsiasi elemento, il `some` restituisce `false`.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `some` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
> [!NOTE]
>  È possibile utilizzare il [metodo every (Array)](../../javascript/reference/every-method-array-javascript.md) per verificare se la funzione di callback restituisce `true` per tutti gli elementi della matrice.  
  
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
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `some`.  
  
|Condizione dopo l'avvio del metodo `some`|Elemento passato alla funzione di callback?|  
|----------------------------------------------|------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa il `some` metodo per determinare se tutti gli elementi in una matrice sono pari.  
  
```JavaScript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `thisArg` parametro che specifica un oggetto a cui il `this` (parola chiave) possono fare riferimento. Controlla se uno dei numeri in una matrice è compreso nell'intervallo fornito da un oggetto passato  
  
```JavaScript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Every (Array)](../../javascript/reference/every-method-array-javascript.md)   
 [Metodo Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Metodo map (Array)](../../javascript/reference/map-method-array-javascript.md)