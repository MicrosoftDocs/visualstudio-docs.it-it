---
title: Metodo getUint16 (DataView) | Documenti Microsoft
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
ms.assetid: 3c0d9ad8-30b0-42a3-b0fe-aa805398c396
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2da1ea7bdbbbc1d99f9b7b6c33e4b3d83e0ba84f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getuint16-method-dataview"></a>Metodo getUint16 (DataView)
Ottiene il valore Uint16 in corrispondenza dell'offset di byte specificata dall'inizio della visualizzazione. È presente alcun vincolo di allineamento; i valori di multi-byte possono essere recuperati dal qualsiasi offset.  
  
## <a name="syntax"></a>Sintassi  
  
```  
var testInt = dataView.getUint16(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parametri  
 `testInt`  
 Obbligatorio. Valore Uint16 restituito dal metodo.  
  
 `byteOffset`  
 Posizione nel buffer in corrispondenza del quale il valore deve essere recuperato.  
  
 `littleEndian`  
 Parametro facoltativo. Se false o non definito, deve essere letto un valore di big-endian, in caso contrario di lettura di un valore di tipo little-endian.  
  
## <a name="remarks"></a>Note  
 Questi metodi generano un'eccezione se sono leggerà oltre la fine della visualizzazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere il primo Uint16 nella vista dati.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint16(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]