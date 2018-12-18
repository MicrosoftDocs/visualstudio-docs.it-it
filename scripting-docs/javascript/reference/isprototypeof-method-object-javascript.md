---
title: Metodo isPrototypeOf (Object) (JavaScript) | Documenti Microsoft
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
- isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isprototypeof-method-object-javascript"></a>Metodo isPrototypeOf (Object) (JavaScript)
Determina se un oggetto esiste nella catena di prototipi di un altro oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>Parametri  
 `prototype`  
 Obbligatorio. Prototipo di oggetto.  
  
 `object`  
 Obbligatorio. Altro oggetto di cui è necessario verificare la catena di prototipi.  
  
## <a name="remarks"></a>Note  
 Il metodo `isPrototypeOf` restituisce `true` se `object` include `prototype` nella catena di prototipi. La catena di prototipi viene utilizzata per condividere funzionalità tra istanze dello stesso tipo di oggetto. Il metodo `isPrototypeOf` restituisce `false` se `object` non è un oggetto oppure se `prototype` non è presente nella catena di prototipi di `object`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `isPrototypeOf`.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)