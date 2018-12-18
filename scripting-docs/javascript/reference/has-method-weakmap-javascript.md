---
title: Metodo has (WeakMap) (JavaScript) | Documenti Microsoft
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakmap-javascript"></a>Metodo has (WeakMap) (JavaScript)
Restituisce `true` se il `WeakMap` oggetto contiene l'elemento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parametri  
 `weakmapObj`  
 Obbligatorio. Oggetto `WeakMap`.  
  
 `key`  
 Obbligatorio. La chiave dell'elemento da testare.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 `true`Se il `WeakMap` contiene la chiave specificata.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere un membro a un `WeakMap` e quindi utilizzare `has` per controllare se è presenta.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]