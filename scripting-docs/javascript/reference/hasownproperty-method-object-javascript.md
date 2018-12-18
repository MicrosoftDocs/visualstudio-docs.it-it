---
title: Metodo hasOwnProperty (Object) (JavaScript) | Documenti Microsoft
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
- hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="hasownproperty-method-object-javascript"></a>Metodo hasOwnProperty (Object) (JavaScript)
Determina se un oggetto ha una proprietà con il nome specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Istanza di un oggetto.  
  
 `proName`  
 Obbligatorio. Valore stringa di un nome di proprietà.  
  
## <a name="remarks"></a>Note  
 Il `hasOwnProperty` restituisce `true` se `object` dispone di una proprietà con il nome specificato, `false` in caso contrario. Questo metodo non controlla le proprietà nella catena di prototipi dell'oggetto; la proprietà deve essere un membro dell'oggetto stesso.  
  
 Questa proprietà non è supportata per gli oggetti host per Internet Explorer 8 e versioni precedenti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, tutte `String` oggetti condividono un metodo split comune. Verrà visualizzato il seguente codice **false** e **true**.  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore in](../../javascript/reference/in-operator-decrementjavascript.md)