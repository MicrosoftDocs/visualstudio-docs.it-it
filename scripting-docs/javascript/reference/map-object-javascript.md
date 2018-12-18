---
title: Oggetto Map (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="map-object-javascript"></a>Oggetto Map (JavaScript)
Raccolta di coppie chiave-valore.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>Note  
 Le chiavi e valori nella raccolta possono essere di qualsiasi tipo. Se si aggiunge un valore alla raccolta utilizzando una chiave esistente, il nuovo valore sostituisce quello vecchio.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Map`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[costruttore](../../javascript/reference/constructor-property-map.md)|Specifica la funzione che crea una mappa.|  
|[prototipo](../../javascript/reference/prototype-property-map.md)|Restituisce un riferimento al prototipo per una mappa.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Restituisce il numero di elementi in una mappa.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Map`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Rimuove tutti gli elementi da una mappa.|  
|[eliminare](../../javascript/reference/delete-method-map-javascript.md)|Rimuove un elemento specificato da una mappa.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Esegue l'azione specificata per ogni elemento in una mappa.|  
|[get](../../javascript/reference/get-method-map-javascript.md)|Restituisce un elemento specificato da una mappa.|  
|[è](../../javascript/reference/has-method-map-javascript.md)|Restituisce `true` se la mappa contiene un elemento specificato.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Aggiunge un nuovo elemento a una mappa.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Restituisce una rappresentazione di stringa di una mappa.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Restituisce il valore primitivo dell'opzione specificata.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto `Map` e quindi recuperarli.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]