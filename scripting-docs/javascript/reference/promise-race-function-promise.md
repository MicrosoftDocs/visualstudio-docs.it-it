---
title: Funzione Promise. race (Promise) | Documenti Microsoft
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d35c448ad143facdcd783df0551505e440521b98
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="promiserace-function-promise"></a>Funzione Promise.race (Promise)
Crea una nuova promessa che sarà risolta o rifiutata con lo stesso valore dei risultati della prima promessa da risolvere o rifiutare tra gli argomenti passati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>Parametri  
 `iterable`  
 Obbligatorio. Una o più promesse.  
  
## <a name="remarks"></a>Note  
 Se una delle promesse in `iterable` è già in uno stato risolto o rifiutato, `Promise.race` restituisce una promessa risolta o rifiutata nello stesso modo con il valore dei risultati uguale al valore usato per risolvere (o rifiutare) la promessa. Se più promesse in `iterable` sono già state risolte o rifiutate, `Promise.race` restituisce una promessa risolta nello stesso modo della prima promessa iterata. Se nessuna promessa in iterable viene risolta o rifiutata, nemmeno la promessa restituita da `Promise.race` viene risolta o rifiutata.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p3 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)
