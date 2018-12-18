---
title: Funzione Promise.All (Promise) | Documenti Microsoft
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="promiseall-function-promise"></a>Funzione Promise.all (Promise)
Unisce due o più promesse e viene restituita solo quando tutte le promesse specificate sono state completate o rifiutate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>Parametri  
 `func1`  
 Obbligatorio. Funzione che restituisce una promessa.  
  
 `func2`  
 Obbligatorio. Funzione che restituisce una promessa.  
  
 `funcN`  
 Parametro facoltativo. Una o più funzioni che restituiscono una promessa.  
  
## <a name="remarks"></a>Note  
 Il risultato restituito è una matrice di valori restituiti dalle promesse completate. Se una delle promesse unite viene rifiutata, la funzione `Promise.all` viene restituita immediatamente con il motivo della promessa rifiutata (tutti gli altri valori restituiti vengono rimossi).  
  
## <a name="example"></a>Esempio  
 In questo codice la prima chiamata a timeout viene restituita dopo 5000 ms. Il gestore di completamento chiama `Promise.all`, che viene restituita solo quando entrambe le chiamate a timeout sono state completate o rifiutate.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)