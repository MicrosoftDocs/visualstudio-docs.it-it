---
title: "Proprietà (UInt32Array) byteOffset | Documenti Microsoft"
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
ms.assetid: 61b1b117-e197-4655-b487-97d08c098775
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4af7bf875d32e4db457c00789b84a42f16fa2b30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="byteoffset-property-uint32array"></a>Proprietà byteOffset (UInt32Array)
Sola lettura. Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var arrayOffset = uint32Array.byteOffset;  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come ottenere l'offset della matrice.  
  
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
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]