---
title: Metodo setUint32 (DataView) | Documenti Microsoft
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
ms.assetid: ab2894fe-4cdc-40c8-9503-951e42ca61e7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e4d2bf075c46f84c75a174b0ca5954b9cedf154
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setuint32-method-dataview"></a>Metodo setUint32 (DataView)
Imposta il valore Uint32 in corrispondenza dell'offset di byte specificata dall'inizio della visualizzazione. È presente alcun vincolo di allineamento; è possibile impostare i valori di multi-byte in corrispondenza di qualsiasi offset.  
  
## <a name="syntax"></a>Sintassi  
  
```  
dataView.setUint32 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Parametri  
 `byteOffset`  
 Posizione nel buffer in corrispondenza del quale il valore deve essere recuperato.  
  
 `value`  
 Il valore da impostare.  
  
 `littleEndian`  
 Parametro facoltativo. Se false o non definito, deve essere scritto un valore big-endian, in caso contrario deve essere scritto un valore di tipo little-endian.  
  
## <a name="remarks"></a>Note  
 Questi metodi generano un'eccezione se scrivono oltre la fine della visualizzazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come impostare il primo Uint32 nella vista dati.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint32(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]