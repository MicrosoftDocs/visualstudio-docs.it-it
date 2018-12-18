---
title: Metodo propertyIsEnumerable (Object) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>Metodo propertyIsEnumerable (Object) (JavaScript)
Determina se una proprietà specificata è enumerabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Istanza di un oggetto.  
  
 `proName`  
 Obbligatorio. Valore stringa di un nome di proprietà.  
  
## <a name="remarks"></a>Note  
 Il `propertyIsEnumerable` restituisce `true` se `proName` esiste `object` e può essere enumerata utilizzando un `For` ciclo. Il `propertyIsEnumerable` restituisce `false` se `object` non dispone di una proprietà con il nome specificato o se la proprietà specificata non è enumerabile. In genere, le proprietà predefinite non sono enumerabile, ma le proprietà definite dall'utente sono sempre enumerabile.  
  
 Il `propertyIsEnumerable` metodo non prende in considerazione gli oggetti nella catena di prototipi.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)