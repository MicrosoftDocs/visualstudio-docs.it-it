---
title: Metodo Add (WeakSet) (JavaScript) | Documenti Microsoft
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-weakset-javascript"></a>Metodo add (WeakSet) (JavaScript)
Aggiunge un nuovo elemento a un oggetto `WeakSet`.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>Parametri  
 `weaksetObj`  
 Obbligatorio. Oggetto `WeakSet`.  
  
 `obj`  
 Obbligatorio. Nuovo elemento dell'oggetto `WeakSet`.  
  
## <a name="remarks"></a>Note  
 Il nuovo elemento deve essere un oggetto, anziché un valore arbitrario, e deve essere univoco. Se si aggiunge un elemento non univoco a `WeakSet`, il nuovo elemento non verrà aggiunto alla raccolta.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come aggiungere membri a un set e verificare che siano stati aggiunti.  
  
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