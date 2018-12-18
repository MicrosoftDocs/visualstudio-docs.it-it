---
title: Funzione Promise. Reject (Promise) | Documenti Microsoft
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="promisereject-function-promise"></a>Funzione Promise.reject (Promise)
Crea una nuova promessa rifiutata con un risultato uguale all'argomento passato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>Parametri  
 `r`  
 Obbligatorio. Il motivo per cui è stata rifiutata la promessa.  
  
## <a name="remarks"></a>Note  
 La funzione di gestione degli errori del metodo `then` o `catch` viene eseguita quando viene restituita la promessa rifiutata.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)