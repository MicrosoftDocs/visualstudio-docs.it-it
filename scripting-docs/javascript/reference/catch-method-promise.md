---
title: Metodo catch (Promise) | Documenti Microsoft
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="catch-method-promise"></a>Metodo catch (Promise)
Consente di specificare il lavoro da eseguire in caso di rifiuto di una promessa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>Parametri  
 `promise`  
 Obbligatorio. Oggetto Promise.  
  
 `onRejected`  
 Obbligatorio. La funzione del gestore errori da eseguire in caso di rifiuto di una promessa.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente, la prima chiamata al timeout viene restituita dopo 5000 ms. In questo codice la promessa viene rifiutata e viene eseguita la funzione del gestore errori.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]