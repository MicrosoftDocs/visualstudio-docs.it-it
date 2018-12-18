---
title: Metodo getInt32 (DataView) | Documenti Microsoft
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
ms.assetid: 7a985681-ddb1-4c2b-815c-514c17392e82
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bae788801a81265d39be5ef090e5820122cbb09b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getint32-method-dataview"></a>Metodo getInt32 (DataView)
Ottiene il valore Int32 in corrispondenza dell'offset di byte specificata dall'inizio della visualizzazione. È presente alcun vincolo di allineamento; i valori di multi-byte possono essere recuperati dal qualsiasi offset.  
  
## <a name="syntax"></a>Sintassi  
  
```  
var testInt = dataView.getInt32(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parametri  
 `testInt`  
 Obbligatorio. Valore Int32 che viene restituito dal metodo.  
  
 `byteOffset`  
 Posizione nel buffer in corrispondenza del quale il valore deve essere recuperato.  
  
 `littleEndian`  
 Parametro facoltativo. Se false o non definito, deve essere letto un valore di big-endian, in caso contrario di lettura di un valore di tipo little-endian.  
  
## <a name="remarks"></a>Note  
 Questi metodi generano un'eccezione se sono leggerà oltre la fine della visualizzazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere il primo Int32 nella vista dati.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt32(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]