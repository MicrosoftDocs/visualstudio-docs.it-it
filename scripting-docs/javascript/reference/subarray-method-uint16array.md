---
title: Metodo (Uint16Array) subarray | Documenti Microsoft
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
ms.assetid: 00b7d3d0-0b47-4da0-95fa-44c9b419d7d0
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ae83767676538e34243096670ba5a52717ebc27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint16array"></a>Metodo subarray (Uint16Array)
Ottiene una nuova visualizzazione Uint16Array del [oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) archiviare per questa matrice, specificando il primo e ultimo membro della sottomatrice.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var newUint16Array = uint16Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parametri  
 `newUint16Array`  
 Sottomatrice restituita da questo metodo.  
  
 `begin`  
 Indice dell'inizio della matrice.  
  
 `end`  
 Indice della fine della matrice. Tale indice non è inclusivo.  
  
## <a name="remarks"></a>Note  
 Se `begin` o `end` è negativo, il valore si riferisce a un indice valutato dalla fine della matrice anziché dall'inizio. Se `end` non è stato specificato, la sottomatrice contiene tutti gli elementi da `begin` alla fine della matrice tipizzata. L'intervallo specificato dai valori di `begin` e `end` viene impostato sull'intervallo valido degli indici per la matrice corrente. Se la lunghezza calcolata della nuova matrice tipizzata è negativa, l'intervallo viene impostato su zero. La matrice restituita è dello stesso tipo della matrice su cui questo metodo è stato invocato.  
  
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
            var intArr = new Uint16Array(buffer.byteLength / 2);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]