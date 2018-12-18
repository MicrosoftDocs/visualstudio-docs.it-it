---
title: Metodo (Uint32Array) subarray | Documenti Microsoft
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
ms.assetid: 4c183208-12ec-4051-bf0f-a4f7c112cea1
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1c76c5c83bcb1e43b51b4f49618e72311d5df86
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint32array"></a>Metodo subarray (Uint32Array)
Ottiene una nuova visualizzazione Uint32Array del [oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) archiviare per questa matrice, specificando il primo e ultimo membro della sottomatrice.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var newUint32Array = uint32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parametri  
 `newUint32Array`  
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
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]