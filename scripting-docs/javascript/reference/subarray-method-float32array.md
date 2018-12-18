---
title: Metodo (Float32Array) subarray | Documenti Microsoft
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
ms.assetid: 97aa27c0-d650-411e-b929-dd9c4a2ae9a5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78d8c729298fe80d841d7c4750e4e6817120c9d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-float32array"></a>Metodo subarray (Float32Array)
Ottiene una nuova visualizzazione Float32Array del [oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) archiviare per questa matrice, specificando il primo e ultimo membro della sottomatrice.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var newFloat32Array = float32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parametri  
 `newFloat32Array`  
 Sottomatrice restituita da questo metodo.  
  
 `begin`  
 Indice dell'inizio della matrice.  
  
 `end`  
 Indice della fine della matrice.  
  
## <a name="remarks"></a>Note  
 Se `begin` o `end` è negativo, il valore si riferisce a un indice valutato dalla fine della matrice anziché dall'inizio. Se `end` non è stato specificato, la sottomatrice contiene tutti gli elementi da `begin` alla fine della matrice tipizzata. L'intervallo specificato dai valori di `begin` e `end` viene impostato sull'intervallo valido degli indici per la matrice corrente. Se la lunghezza calcolata della nuova matrice tipizzata è negativa, l'intervallo viene impostato su zero. La matrice restituita è dello stesso tipo della matrice su cui questo metodo è stato invocato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere una sottomatrice di tre elementi a partire dal primo elemento della matrice.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]