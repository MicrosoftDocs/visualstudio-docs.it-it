---
title: Oggetto WeakMap (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>Oggetto WeakMap (JavaScript)
Raccolta di coppie chiave-valore in cui ogni chiave è un riferimento a un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>Note  
 Oggetto `WeakMap` oggetto non può essere enumerato.  
  
 Se si aggiunge un valore alla raccolta utilizzando una chiave esistente, il nuovo valore sostituisce quello vecchio.  
  
 In un `WeakMap` dell'oggetto, i riferimenti agli oggetti principali contenuti 'debole'. Ciò significa che `WeakMap` non impedisce un'operazione di garbage collection sugli oggetti chiavi. Quando non sono presenti riferimenti (diversi da `WeakMap`) agli oggetti chiavi, il garbage collector potrebbe raccogliere gli oggetti chiavi.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `WeakMap`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[costruttore](../../javascript/reference/constructor-property-weakmap.md)|Specifica la funzione che crea un oggetto `WeakMap`.|  
|[prototipo](../../javascript/reference/prototype-property-weakmap.md)|Restituisce un riferimento al prototipo per un oggetto `WeakMap`.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `WeakMap`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Rimuove tutti gli elementi da `WeakMap`.|  
|[eliminare](../../javascript/reference/delete-method-weakmap-javascript.md)|Rimuove un elemento specificato da un `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Restituisce un elemento specificato da un `WeakMap`.|  
|[è](../../javascript/reference/has-method-weakmap-javascript.md)|Restituisce `true` se il `WeakMap` contiene un elemento specificato.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Aggiunge un nuovo elemento a un oggetto `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Restituisce una rappresentazione di stringa di un `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Restituisce il valore primitivo dell'opzione specificata.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un `WeakMap` dell'oggetto e quindi recuperarli.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]