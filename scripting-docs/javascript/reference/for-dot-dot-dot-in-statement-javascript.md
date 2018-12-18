---
title: for.... nell'istruzione (JavaScript) | Documenti Microsoft
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
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="forin-statement-javascript"></a>Istruzione for...in (JavaScript)
Esegue uno o più istruzioni per ogni proprietà di un oggetto o di ogni elemento della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parametri  
 `variable`  
 Obbligatorio. Una variabile che può essere qualsiasi nome di proprietà di `object` o qualsiasi indice di elemento di un `array`.  
  
 `object`, `array`  
 Parametro facoltativo. Un oggetto o una matrice su cui eseguire l'iterazione.  
  
 `statements`  
 Parametro facoltativo. Una o più istruzioni da eseguire per ogni proprietà di `object` o di ogni elemento di `array`. Può essere un'istruzione composta.  
  
## <a name="remarks"></a>Note  
 All'inizio di ogni iterazione di un ciclo, il valore di `variable` è il nome della proprietà successivo `object` o l'indice di elemento successivo del `array`. È quindi possibile utilizzare `variable` in una qualsiasi delle istruzioni all'interno del ciclo per fare riferimento alla proprietà di `object` o all'elemento di `array`.  
  
 Le proprietà di un oggetto non sono assegnate in un determinato modo. È possibile specificare una determinata proprietà mediante il relativo indice, solo il nome della proprietà.  
  
 Viene eseguito lo scorrimento di una matrice in ordine degli elementi, ovvero 0, 1, 2.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `for...in` istruzione con un oggetto utilizzato come matrice associativa.  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato l'utilizzo del `for ... in` istruzione per scorrere un `Array` oggetto contenente le proprietà expando.  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Utilizzare il `Enumerator` oggetto per scorrere i membri di una raccolta.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)