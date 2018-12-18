---
title: Istruzione switch (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="switch-statement-javascript"></a>Istruzione switch (JavaScript)
Consente l'esecuzione di una o più istruzioni quando il valore dell'espressione specificata corrisponde a un'etichetta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>Parametri  
 `expression`  
 L'espressione da valutare.  
  
 `label`  
 Un identificatore che deve corrispondere `expression`. Se `label` è un `expression`, inizia l'esecuzione con il `statementlist` subito dopo i due punti e continua finché incontra uno un `break` istruzione, che è facoltativo, o alla fine del `switch` istruzione.  
  
 `statementlist`  
 Una o più istruzioni da eseguire.  
  
## <a name="remarks"></a>Note  
 Utilizzare il `default` clausola per specificare l'istruzione da eseguire se nessuno dell'etichetta valori corrispondenze `expression`. Può trovarsi in qualsiasi punto all'interno di `switch` blocco di codice.  
  
 Zero o più `label` blocchi possono essere specificati. Se non `label` corrisponde al valore di `expression`e un `default` caso non viene fornito, viene eseguita alcuna istruzione.  
  
 Flusso di esecuzione di un `switch` come segue:  
  
-   Valutare `expression` ed esaminare `label` in ordine fino a quando non viene trovata una corrispondenza.  
  
-   Se un `label` valore è uguale a `expression`, eseguire il relativo tipo di accompagnamento `statementlist`.  
  
     Continuare l'esecuzione fino a quando un `break` viene rilevata l'istruzione, o `switch` fine dell'istruzione. Ciò significa che più `label` i blocchi vengono eseguiti se un `break` non viene utilizzata l'istruzione.  
  
-   Se non `label` è uguale a `expression`, visitare il `default` case. Se è presente alcun `default` caso, andare al passaggio precedente.  
  
-   Continuare l'esecuzione in corrispondenza dell'istruzione successiva alla fine del `switch` blocco di codice.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente verifica il tipo di un oggetto.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="example"></a>Esempio  
 Il codice seguente mostra cosa accade se non si utilizza un `break` istruzione.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)