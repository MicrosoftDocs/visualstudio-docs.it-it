---
title: Metodo Call (Function) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="call-method-function-javascript"></a>Metodo call (Function) (JavaScript)
Chiama un metodo di un oggetto, sostituendo un altro oggetto per l'oggetto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 `thisObj`  
 Parametro facoltativo. Oggetto da utilizzare come oggetto corrente.  
  
 `arg1, arg2, , argN`  
 Parametro facoltativo. Un elenco di argomenti da passare al metodo.  
  
## <a name="remarks"></a>Note  
 Il `call` metodo viene utilizzato per chiamare un metodo per conto di un altro oggetto. Consente di modificare il `this` oggetto di una funzione dal contesto originale al nuovo oggetto specificato da `thisObj`.  
  
 Se `thisObj` non viene fornito il `global` oggetto viene utilizzato come `thisObj`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come utilizzare il metodo `call`.  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Metodo apply (Function)](../../javascript/reference/apply-method-function-javascript.md)