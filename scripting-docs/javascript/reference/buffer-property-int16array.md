---
title: "Proprietà (Int16Array) buffer | Documenti Microsoft"
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
ms.assetid: 22117ad2-d865-47be-b15e-8181de257672
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 781af9b285af84acff5f268c6a6de821a48681fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="buffer-property-int16array"></a>Proprietà buffer (Int16Array)
Sola lettura. Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var arrayBuffer = int16Array.buffer;  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come ottenere l'oggetto ArrayBuffer della matrice.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int16Array(buffer.byteLength / 2);  
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]