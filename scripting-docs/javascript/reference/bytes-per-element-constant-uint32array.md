---
title: Costante BYTES_PER_ELEMENT (Uint32Array) | Documenti Microsoft
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
ms.assetid: 9a82d1bf-0e97-4e14-b86f-343ccc8dfac2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6406a1c44117718fe368bbacad96956a6f17616
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bytesperelement-constant-uint32array"></a>Costante BYTES_PER_ELEMENT (Uint32Array)
Dimensione in byte di ogni elemento nella matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var arraySize = uint32Array.BYTES_PER_ELEMENT;  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere la dimensione degli elementi della matrice.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]