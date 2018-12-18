---
title: Metodo forEach (Map) (JavaScript) | Documenti Microsoft
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d0ffa12b9a1995df14f4868872238cdc45b674a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-map-javascript"></a>Metodo forEach (Map) (JavaScript)
Esegue l'azione specificata per ogni elemento in una mappa.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametri  
 `mapObj`  
 Obbligatorio. Oggetto `Map`.  
  
 `callbackfn`  
 Obbligatorio. La funzione che `forEach` chiama una volta per ogni elemento nella mappa. `callbackfn`accetta fino a tre argomenti. `forEach`chiamate di `callbackfn` funzione una sola volta per ogni elemento nella mappa.  
  
 `thisArg`  
 Parametro facoltativo. Un oggetto che il `this` (parola chiave) possono fare riferimento al `callbackfn` (funzione). Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.  
  
## <a name="exceptions"></a>Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## <a name="remarks"></a>Note  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, key, mapObj)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a tre parametri, come illustrato nella tabella seguente.  
  
|Argomento di callback|Definizione|  
|-----------------------|----------------|  
|`value`|Un valore contenuto nella mappa.|  
|`key`|Una chiave contenuta nella mappa.|  
|`mapObj`|Il `Map` oggetto da attraversare.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come recuperare i membri di un `Map` utilizzando `forEach`.  
  
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