---
title: Funzione Promise. Resolve (Promise) | Documenti Microsoft
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="promiseresolve-function-promise"></a>Funzione Promise.resolve (Promise)
Crea una nuova promessa risolta con un risultato uguale al relativo argomento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>Parametri  
 `x`  
 Obbligatorio. Valore restituito della promessa completata.  
  
## <a name="remarks"></a>Note  
 La funzione di gestione dell'evasione del metodo `then` viene eseguita alla restituzione dell'oggetto promise completato.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)