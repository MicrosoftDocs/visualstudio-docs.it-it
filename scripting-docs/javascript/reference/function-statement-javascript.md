---
title: funzione istruzione (JavaScript) | Documenti Microsoft
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
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="function-statement-javascript"></a>Istruzione function (JavaScript)
Dichiara una nuova funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parametri  
 `functionname`  
 Obbligatorio. Nome della funzione.  
  
 `arg1...argN`  
 Parametro facoltativo. Un elenco facoltativo delimitato da virgole degli argomenti che la funzione è in grado di comprendere.  
  
 `statements`  
 Parametro facoltativo. Uno o più[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] istruzioni.  
  
## <a name="remarks"></a>Note  
 Utilizzare il `function` istruzione per dichiarare una funzione per un uso successivo. Il codice contenuto in `statements` non viene eseguito fino a quando la funzione viene chiamata da in un' posizione nello script.  
  
 Il [restituire](../../javascript/reference/return-statement-javascript.md) istruzione viene utilizzata per restituire un valore dalla funzione. Non è necessario utilizzare un `return` istruzione; il programma verrà eseguito quando raggiunge la fine della funzione. Se non `return` viene eseguita un'istruzione nella funzione, o se il `return` istruzione è presente alcuna espressione, la funzione restituisce il valore `undefined`.  
  
> [!NOTE]
>  Quando si chiama una funzione, assicurarsi di includere le parentesi e gli argomenti richiesti. Chiamata di una funzione senza parentesi restituisce un riferimento alla funzione, non i risultati della funzione.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `function`.  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>Esempio  
 Una funzione può essere assegnata a una variabile. Questa procedura è illustrata nell'esempio riportato di seguito.  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)