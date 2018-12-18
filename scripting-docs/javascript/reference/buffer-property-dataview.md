---
title: "Proprietà buffer (DataView) | Documenti Microsoft"
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
ms.assetid: b69afc28-586e-4277-8cd6-b9d69a54fb55
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83dae7c89ba4ae943d04efc92ca637e0d7447ec4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="buffer-property-dataview"></a>Proprietà buffer (DataView)
Sola lettura. Ottiene l'oggetto ArrayBuffer a cui fa riferimento da questa vista.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var arrayBuffer = dataView.buffer;  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere la lunghezza di ArrayBuffer sottostante DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.buffer.byteLength)  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]