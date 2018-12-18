---
title: Metodo slice (ArrayBuffer) | Documenti Microsoft
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-arraybuffer"></a>Metodo slice (ArrayBuffer)
Restituisce una sezione di un [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parametri  
 `arrayBufferObj`  
 Obbligatorio. Il [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) la sezione verrà copiata dall'oggetto.  
  
 `start`  
 Obbligatorio. Indice byte dell'inizio della sezione da copiare.  
  
 `end`  
 Facoltativo. Indice byte della fine della sezione da copiare.  
  
## <a name="remarks"></a>Note  
 Il `slice` metodo restituisce un [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) oggetto che contiene la parte specificata di `arrayBufferObj`.  
  
 Il metodo `slice` copia, senza includerlo, fino al byte indicato da `end`. Se `start` o `end` è negativo, corrispondenza dell'indice specificato viene considerato come `length`  +  `start` o `end`, rispettivamente, in cui `length` è la lunghezza del [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). Se `end` viene omesso, l'estrazione continua fino alla fine di `arrayBufferObj`. Se `end` si verifica prima `start`, non vengono copiati byte nel nuovo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="example"></a>Esempio  
 Gli esempi seguenti mostrano come usare il metodo `slice`.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)