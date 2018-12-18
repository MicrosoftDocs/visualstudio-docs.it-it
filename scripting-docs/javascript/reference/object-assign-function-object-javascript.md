---
title: Funzione Object. ASSIGN (Object) (JavaScript) | Documenti Microsoft
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectassign-function-object-javascript"></a>Funzione Object.assign (Object) (JavaScript)
Copia i valori da uno o più oggetti di origine in un oggetto di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>Parametri  
 `target`  
 Obbligatorio. Oggetto in cui vengono copiate le proprietà enumerabili.  
  
 `...sources`  
 Obbligatorio. Uno o più oggetti da cui vengono copiate le proprietà enumerabili.  
  
## <a name="exceptions"></a>Eccezioni  
 Questa funzione genera un `TypeError` se si verifica un errore di assegnazione, che termina l'operazione di copia. Se una proprietà di destinazione non è scrivibile, verrà generato un `TypeError`.  
  
## <a name="remarks"></a>Note  
 Questa funzione restituisce l'oggetto di destinazione. Solo *enumerabile proprio* le proprietà vengono copiate dall'oggetto di origine all'oggetto di destinazione. È possibile usare questa funzione per unire o clonare oggetti.  
  
 Le origini `null` o `undefined` vengono considerate come oggetti vuoti e non forniscono alcun contributo all'oggetto di destinazione.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come unire un oggetto tramite `Object.assign`.  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come clonare un oggetto tramite `Object.assign`.  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]