---
title: Operatore Spread (...) (JavaScript) | Documenti Microsoft
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="spread-operator--javascript"></a>Operatore spread (...) (JavaScript)
Consente di inizializzare parti di un valore letterale della matrice da un'espressione iterabile (come un altro valore letterale della matrice) oppure di espandere un'espressione in più argomenti (in chiamate di funzione).  
  
## <a name="syntax"></a>Sintassi  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>Parametri  
 `iterable`  
 Obbligatorio. Oggetto iterabile.  
  
 `arg0ToN`  
 Parametro facoltativo. Uno o più elementi di un valore letterale della matrice.  
  
 `args`  
 Parametro facoltativo. Uno o più argomenti di una funzione.  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sugli iteratori, vedere [iteratori e generatori](../../javascript/advanced/iterators-and-generators-javascript.md). Per ulteriori informazioni sull'utilizzo dell'operatore spread come parametro rest, vedere [funzioni](../../javascript/functions-javascript.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente vengono illustrate le differenze tra dell'operatore spread e il metodo `concat`.  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato l'uso dell'operatore spread in una chiamata di funzione. In questo esempio due valori letterali della matrice vengono passati alla funzione tramite l'operatore spread e le due matrici vengono espanse in più argomenti.  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>Esempio  
 Con gli operatori spread è possibile semplificare il codice per il quale in precedenza era necessario usare `apply`.  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)