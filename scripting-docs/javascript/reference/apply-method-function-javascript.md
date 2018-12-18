---
title: Metodo Apply (Function) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- apply
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Apply method
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a06a37006937b07214bf5a314d5151c3b658acf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="apply-method-function-javascript"></a>Metodo apply (Function) (JavaScript)
Chiama la funzione, sostituendo l'oggetto specificato per il `this` valore della funzione e la matrice specificata per gli argomenti della funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
apply([thisObj[,argArray]])  
```  
  
## <a name="parameters"></a>Parametri  
 `thisObj`  
 Parametro facoltativo. L'oggetto da utilizzare come il `this` oggetto.  
  
 `argArray`  
 Parametro facoltativo. Un set di argomenti da passare alla funzione.  
  
## <a name="remarks"></a>Note  
 Se `argArray` non è un oggetto valido, quindi si verifica un errore "Oggetto previsto".  
  
 Se non si specifica `argArray` né `thisObj` vengono forniti originale `this` oggetto viene utilizzato come `thisObj` e non vengono passati argomenti.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare il metodo apply.  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)