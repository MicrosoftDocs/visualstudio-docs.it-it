---
title: Metodo shift (Array) (JavaScript) | Documenti Microsoft
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
- shift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- shift method
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c3f764950b329cea8356f5b350ee917f0a60f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="shift-method-array-javascript"></a>Metodo shift (Array) (JavaScript)
Rimuove il primo elemento di una matrice e lo restituisce.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.shift( )  
```  
  
#### <a name="parameters"></a>Parametri  
 Obbligatorio `arrayObj` riferimento è un `Array` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce l'elemento rimosso dalla matrice.  
  
## <a name="remarks"></a>Note  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `shift`.  
  
```JavaScript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo unshift (Array)](../../javascript/reference/unshift-method-array-javascript.md)