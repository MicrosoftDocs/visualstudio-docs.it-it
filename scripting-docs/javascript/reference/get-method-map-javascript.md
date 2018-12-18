---
title: Metodo Get (Map) (JavaScript) | Documenti Microsoft
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-map-javascript"></a>Metodo get (Map) (JavaScript)
Restituisce un elemento specificato da una mappa.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>Parametri  
 `mapObj`  
 Obbligatorio. Oggetto `Map`.  
  
 `key`  
 Obbligatorio. La chiave di un elemento di `Map`.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Restituisce l'oggetto associato alla chiave. Se il `Map` non contiene la chiave, questo metodo restituisce un `undefined` valore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come recuperare un elemento da un `Map` oggetto.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]