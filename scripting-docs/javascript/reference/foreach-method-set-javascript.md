---
title: Metodo forEach (Set) (JavaScript) | Documenti Microsoft
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-set-javascript"></a>Metodo forEach (Set) (JavaScript)
Esegue l'azione specificata per ogni elemento in un set.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametri  
 `setObj`  
 Obbligatorio. Oggetto `Set`.  
  
 `callbackfn`  
 Obbligatorio. `callbackfn`accetta fino a tre argomenti. La funzione che `forEach` chiama una volta per ogni elemento nel set.  
  
 `thisArg`  
 Parametro facoltativo. Un oggetto che il `this` (parola chiave) possono fare riferimento al `callbackfn` (funzione). Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.  
  
## <a name="exceptions"></a>Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## <a name="remarks"></a>Note  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, key, setObj)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a tre parametri, come illustrato nella tabella seguente.  
  
|Argomento di callback|Definizione|  
|-----------------------|----------------|  
|`value`|Un valore incluso nel set.|  
|`key`|Un valore incluso nel set. Un set non è presenti chiavi, pertanto questo valore è lo stesso come `value`.|  
|`setObj`|Il `Set` oggetto da attraversare.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come usare `forEach`. Il `callbackfn` argomento include il codice per la funzione di callback.  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato che è anche possibile recuperare i membri da un set passando un solo parametro alla funzione di callback.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]