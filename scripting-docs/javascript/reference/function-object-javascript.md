---
title: Funzione Object (JavaScript) | Documenti Microsoft
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
- function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="function-object-javascript"></a>Oggetto Function (JavaScript)
Crea una nuova funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>Parametri  
 `functionName`  
 Obbligatorio. Il nome della funzione appena creata.  
  
 `argname1...argnameN`  
 Parametro facoltativo. Un elenco di argomenti accettati dalla funzione.  
  
 `body`  
 Parametro facoltativo. Stringa che contiene il blocco di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice da eseguire quando viene chiamata la funzione.  
  
## <a name="remarks"></a>Note  
 La funzione è un tipo di dati di base in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. La sintassi 1 crea un valore di funzione [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte in un `Function` dell'oggetto quando necessario. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Converte `Function` degli oggetti creati da 2 di sintassi nei valori di funzione al momento la funzione viene chiamata.  
  
 La sintassi 1 è la modalità standard di creazione di nuove funzioni in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. La sintassi 2 è un tipo alternativo utilizzato per creare gli oggetti funzione in modo esplicito.  
  
 Ad esempio, per dichiarare una funzione che aggiunge i due argomenti passati a esso, è possibile farlo in uno dei due modi:  
  
## <a name="example-1"></a>Esempio 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>Esempio 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 In entrambi i casi, si chiama la funzione con una riga di codice simile al seguente:  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  Quando si chiama una funzione, assicurarsi di includere sempre le parentesi e gli argomenti richiesti. Chiamata di una funzione senza parentesi fa sì che la funzione stessa da restituire, anziché il valore restituito della funzione.  
  
## <a name="properties"></a>Proprietà  
 [0... n proprietà](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[ Proprietà arguments](../../javascript/reference/arguments-property-function-javascript.md) &#124; [proprietà callee](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [proprietà caller](../../javascript/reference/caller-property-function-javascript.md) &#124; [proprietà constructor](../../javascript/reference/constructor-property-object-javascript.md) &#124; [proprietà length (Function)](../../javascript/reference/length-property-function-javascript.md) &#124; [proprietà prototype](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>Metodi  
 [Metodo Apply](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind (metodo)](../../javascript/reference/bind-method-function-javascript.md) &#124; [metodo](../../javascript/reference/call-method-function-javascript.md) &#124; [metodo toString](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf (metodo)](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione Function](../../javascript/reference/function-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Istruzione var](../../javascript/reference/var-statement-javascript.md)