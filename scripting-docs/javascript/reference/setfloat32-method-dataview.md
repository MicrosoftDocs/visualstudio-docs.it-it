---
title: Metodo setFloat32 (DataView) | Documenti Microsoft
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
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a72bf2781bfbae7c7cd301d02ad71ebfbeffa13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setfloat32-method-dataview"></a>Metodo setFloat32 (DataView)
Imposta il valore Float32 in corrispondenza dell'offset di byte specificata dall'inizio della visualizzazione. È presente alcun vincolo di allineamento; è possibile impostare i valori di multi-byte in corrispondenza di qualsiasi offset.  
  
## <a name="syntax"></a>Sintassi  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
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
 Nell'esempio seguente viene illustrato come impostare il primo Float32 nella vista dati.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat32(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]