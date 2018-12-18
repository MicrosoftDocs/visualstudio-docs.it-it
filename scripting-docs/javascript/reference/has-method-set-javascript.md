---
title: Metodo has (Set) (JavaScript) | Documenti Microsoft
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-set-javascript"></a>Metodo has (Set) (JavaScript)
Restituisce `true` se il set contiene l'elemento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>Parametri  
 `setObj`  
 Obbligatorio. Oggetto `Set`.  
  
 `value`  
 Obbligatorio. Elemento su cui eseguire il test.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 `true` se il set contiene l'elemento specificato.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come aggiungere membri a un oggetto `Set` e quindi verificare se il set contiene un membro specifico.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]