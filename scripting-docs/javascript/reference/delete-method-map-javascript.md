---
title: Metodo Delete (Map) (JavaScript) | Documenti Microsoft
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5185b883cf603acdc91fe1f1c833d337c4468ba4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-map-javascript"></a>Metodo delete (Map) (JavaScript)
Rimuove l'elemento specificato da una mappa.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
mapObj.delete(key)  
```  
  
#### <a name="parameters"></a>Parametri  
 `mapObj`  
 Obbligatorio. Oggetto `Map`.  
  
 `key`  
 Obbligatorio. Chiave dell'elemento da rimuovere.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 `true` se l'elemento è stato rimosso.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un `Map` e quindi si elimina uno di essi.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]