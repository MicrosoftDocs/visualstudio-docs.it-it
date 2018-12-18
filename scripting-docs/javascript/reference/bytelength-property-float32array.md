---
title: "Proprietà (Float32Array) byteLength | Documenti Microsoft"
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
ms.assetid: ea55beb2-e79f-4706-bcc9-6fdbf89e0fe9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c4b403a6632b143961df541dc13b03c9208d274
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-float32array"></a>Proprietà byteLength (Float32Array)
Sola lettura. Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var arrayByteLength = float32Array.byteLength;  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere la lunghezza della matrice.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float32Array(buffer.byteLength) / 4);  
            alert(floatArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]