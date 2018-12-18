---
title: Metodo has (WeakSet) (JavaScript) | Documenti Microsoft
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dbc7e17e3fd73730386293c5e3f894455e41a93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakset-javascript"></a>Metodo has (WeakSet) (JavaScript)
Restituisce `true` se `WeakSet` contiene l'elemento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
setObj.has(obj)  
```  
  
#### <a name="parameters"></a>Parametri  
 `setObj`  
 Obbligatorio. Oggetto `WeakSet`.  
  
 `obj`  
 Obbligatorio. Elemento su cui eseguire il test.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 `true` se il set contiene l'elemento specificato.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come aggiungere membri a un oggetto `WeakSet` e quindi verificare se il set contiene un membro specifico.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]