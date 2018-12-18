---
title: impostare il metodo (Uint8ClampedArray) | Documenti Microsoft
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed7635559e615746c577560f1a9266b26acd959d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-uint8clampedarray"></a>Metodo set (Uint8ClampedArray)
Imposta un valore o una matrice di valori.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
uint8ClampedArray.set(index, value);  
uint8ClampedArray.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Parametri  
 `index`  
 Indice della posizione da impostare.  
  
 `value`  
 Valore da impostare.  
  
 `array`  
 Matrice tipizzata o non tipizzata di valori da impostare.  
  
 `offset`  
 Indice nella matrice corrente in base al quale devono essere scritti i valori.  
  
## <a name="remarks"></a>Note  
 Se la matrice di input è una matrice tipizzata, le due matrici possono utilizzare sottostante stesso [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). In questa situazione l'impostazione dei valori viene eseguita come se tutti i dati fossero stati prima copiati in un buffer temporaneo che non si sovrappone ad alcuna matrice e come se successivamente i dati presenti nel buffer temporaneo venissero copiati nella matrice corrente.  
  
 Se il valore ottenuto sommando l'offset e la lunghezza della matrice specificata non è compreso nell'intervallo per la matrice tipizzata corrente, viene generata un'eccezione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come impostare il primo elemento della matrice.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Oggetto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)