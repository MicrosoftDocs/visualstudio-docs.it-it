---
title: Metodo Delete (WeakMap) (JavaScript) | Documenti Microsoft
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4cec06b77b7198e23d7e455849b5c0bf6d7ff9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-weakmap-javascript"></a>Metodo delete (WeakMap) (JavaScript)
Rimuove l'elemento specificato da un oggetto `WeakMap`.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
weakmapObj.delete(key)  
```  
  
#### <a name="parameters"></a>Parametri  
 `weakmapObj`  
 Obbligatorio. Oggetto `WeakMap`.  
  
 `key`  
 Obbligatorio. Chiave dell'elemento da rimuovere.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 `true` se l'elemento è stato rimosso.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere un membro a un `WeakMap` e quindi eliminarlo.  
  
```JavaScript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]