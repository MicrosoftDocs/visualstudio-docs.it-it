---
title: Get (metodo) (Float64Array) | Documenti Microsoft
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
ms.assetid: debbe2f4-fe1e-4f9d-af7d-b24430bfa962
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bee0ffe2417c8cc2743f9fd35d74899a940dde6e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-float64array"></a>Metodo get (Float64Array)
Può essere omesso. Ottiene l'elemento in corrispondenza dell'indice specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
var value = float64Array.get(index);  
```  
  
## <a name="parameters"></a>Parametri  
 `value`  
 Valore restituito da questo metodo.  
  
 `index`  
 Indice in corrispondenza del quale ottenere l'elemento della matrice.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere il primo elemento della matrice.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 4);  
            var element = floatArr.getFloat64(0);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]