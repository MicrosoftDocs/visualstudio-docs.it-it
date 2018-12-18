---
title: Metodo reverse (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="reverse-method-javascript"></a>Metodo reverse (JavaScript)
Inverte gli elementi in un `Array`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Qualsiasi oggetto `Array`.  
  
## <a name="return-value"></a>Valore restituito  
 La matrice invertita.  
  
## <a name="remarks"></a>Note  
 Obbligatorio `arrayObj` riferimento è un `Array` oggetto.  
  
 Il `reverse` metodo inverte gli elementi di un `Array` oggetto sul posto. Non viene creato un nuovo `Array` oggetto durante l'esecuzione.  
  
 Se la matrice non è contigua, la `reverse` metodo crea gli elementi nella matrice di riempire i gap nella matrice. Ognuno di questi elementi creati con il valore `undefined`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `reverse`.  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo concat (Array)](../../javascript/reference/concat-method-array-javascript.md)