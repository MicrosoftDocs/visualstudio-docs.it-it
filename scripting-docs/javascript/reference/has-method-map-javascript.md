---
title: Metodo has (Map) (JavaScript) | Documenti Microsoft
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-map-javascript"></a>Metodo has (Map) (JavaScript)
Restituisce `true` se la mappa contiene l'elemento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parametri  
 `mapObj`  
 Obbligatorio. Oggetto `Map`.  
  
 `key`  
 Obbligatorio. La chiave dell'elemento da testare.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 `true`Se la mappa contiene l'elemento specificato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere un membro a un `Map` , quindi verificare se contiene la mappa.  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]