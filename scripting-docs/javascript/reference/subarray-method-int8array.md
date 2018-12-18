---
title: Metodo (Int8Array) subarray | Documenti Microsoft
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-int8array"></a>Metodo subarray (Int8Array)
Ottiene una nuova visualizzazione Int8Array dell'archivio ArrayBuffer per questa matrice, facendo riferimento agli elementi dall'inizio (inclusi) alla fine (esclusi).  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>Parametri  
 `newInt8Array`  
 Sottomatrice restituita da questo metodo.  
  
 `begin`  
 Indice dell'inizio della matrice.  
  
 `end`  
 Indice della fine della matrice. Tale indice non è inclusivo.  
  
## <a name="remarks"></a>Note  
 Se l'inizio o la fine è negativo, si riferisce a un indice considerato dalla fine della matrice anziché dall'inizio. Se la fine non è specificata, la sottomatrice contiene tutti gli elementi dall'inizio alla fine di TypedArray. L'intervallo specificato dai valori iniziale e finale viene impostato sull'intervallo valido degli indici della matrice corrente. Se la lunghezza calcolata del nuovo oggetto TypedArray è negativa, l'intervallo viene impostato su zero. Il tipo dell'oggetto TypedArray restituito sarà uguale a quello della matrice in cui viene richiamato questo metodo.  
  
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
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]