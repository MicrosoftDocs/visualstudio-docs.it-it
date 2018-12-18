---
title: Metodo (Uint8ClampedArray) subarray | Documenti Microsoft
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cda8b123b02b4c19a7fd162f3bfbce4540d149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint8clampedarray"></a>Metodo subarray (Uint8ClampedArray)
Ottiene un nuovo [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) visualizzare il [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) archiviare per questa matrice, specificando il primo e ultimo membro della sottomatrice.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parametri  
 `newUint8ClampedArray`  
 Obbligatorio. Sottomatrice restituita da questo metodo.  
  
 `begin`  
 Facoltativo. Indice dell'inizio della matrice.  
  
 `end`  
 Facoltativo. Indice della fine della matrice. Tale indice non è inclusivo.  
  
## <a name="remarks"></a>Note  
 Se `begin` o `end` è negativo, il valore si riferisce a un indice valutato dalla fine della matrice anziché dall'inizio. Se `end` non è stato specificato, la sottomatrice contiene tutti gli elementi da `begin` alla fine della matrice tipizzata. L'intervallo specificato dai valori di `begin` e `end` viene impostato sull'intervallo valido degli indici per la matrice corrente. Se la lunghezza calcolata della nuova matrice tipizzata è negativa, l'intervallo viene impostato su zero. La matrice restituita è dello stesso tipo della matrice su cui è stato richiamato questo metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente esempio viene mostrato come è possibile ottenere una sottomatrice di due elementi a partire dal primo elemento della matrice.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Oggetto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)