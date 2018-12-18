---
title: Metodo Delete (Set) (JavaScript) | Documenti Microsoft
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-set-javascript"></a>Metodo delete (Set) (JavaScript)
Rimuove l'elemento specificato da un set.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>Parametri  
 `setObj`  
 Obbligatorio. Oggetto `Set`.  
  
 `value`  
 Obbligatorio. Elemento da rimuovere.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 `true` se l'elemento è stato rimosso.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un `Set` e quindi si elimina uno di essi.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]