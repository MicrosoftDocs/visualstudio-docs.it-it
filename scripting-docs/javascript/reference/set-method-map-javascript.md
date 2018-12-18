---
title: Metodo set (Map) (JavaScript) | Documenti Microsoft
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-map-javascript"></a>Metodo set (Map) (JavaScript)
Aggiunge un nuovo elemento a una mappa.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parametri  
 `mapObj`  
 Obbligatorio. Oggetto `Map`.  
  
 `key`  
 Obbligatorio. Chiave per il nuovo elemento.  
  
 `value`  
 Obbligatorio. Valore dell'elemento da aggiungere.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Restituisce l'oggetto `Map` che contiene la nuova coppia chiave/valore.  
  
## <a name="remarks"></a>Note  
 Se si aggiunge un valore alla raccolta utilizzando una chiave esistente, il nuovo valore sostituisce quello vecchio.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto `Map` e quindi recuperarli.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]