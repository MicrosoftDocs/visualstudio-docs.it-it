---
title: for.... dell'istruzione (JavaScript) | Documenti Microsoft
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47154261fd4817ba95b8884bd6482a87e044a5a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="forof-statement-javascript"></a>Istruzione for...of (JavaScript)
Esegue una o più istruzioni per ogni valore di un iteratore ottenuto da un oggetto iterabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parametri  
 `variable`  
 Obbligatorio. Una variabile che può essere qualsiasi valore della proprietà di `object`.  
  
 `object`  
 Obbligatorio. Un oggetto iterabile, ad esempio un `Array`, `Map`, `Set`, o un oggetto che implementa il [interfacce iteratore](http://msdn.microsoft.com/en-us/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Parametro facoltativo. Una o più istruzioni da eseguire per ogni valore di `object`. Può essere un'istruzione composta.  
  
## <a name="remarks"></a>Note  
 All'inizio di ogni iterazione di un ciclo, il valore di `variable` è il successivo valore della proprietà di `object`.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'uso dell'istruzione `for...of` in una matrice.  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'uso dell'istruzione `for...of` in un oggetto `Map`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [for.... nell'istruzione](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)