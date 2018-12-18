---
title: Metodo set (WeakMap) (JavaScript) | Documenti Microsoft
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-weakmap-javascript"></a>Metodo set (WeakMap) (JavaScript)
Aggiunge un nuovo elemento a un oggetto `WeakMap`.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parametri  
 `weakmapObj`  
 Obbligatorio. Oggetto `WeakMap`.  
  
 `key`  
 Obbligatorio. Oggetto che rappresenta la chiave dell'elemento da aggiungere. Deve essere un riferimento a un oggetto.  
  
 `value`  
 Obbligatorio. Valore dell'elemento da aggiungere.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Restituisce l'oggetto `WeakMap` che contiene la nuova coppia chiave/valore.  
  
## <a name="remarks"></a>Note  
 Se si aggiunge un valore alla raccolta utilizzando una chiave esistente, il nuovo valore sostituisce quello vecchio.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto `WeakMap`.  
  
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
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]