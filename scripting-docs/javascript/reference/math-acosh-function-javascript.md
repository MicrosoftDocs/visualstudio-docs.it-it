---
title: Funzione Math. Acosh (JavaScript) | Documenti Microsoft
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Funzione Math.acosh (JavaScript)
Restituisce l'arcocoseno iperbolico (o coseno iperbolico inverso) di un numero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>Parametri  
 L'argomento `number` obbligatorio è un'espressione numerica.  
  
## <a name="return-value"></a>Valore restituito  
 Coseno iperbolico inverso dell'argomento `number`, in radianti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come usare la funzione `acosh`.  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>Note  
 **Si applica a**: [Math (oggetto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Math. Acos](../../javascript/reference/math-acos-function-javascript.md)   
 [Funzione Math. asin](../../javascript/reference/math-asin-function-javascript.md)   
 [Funzione Math. Atan](../../javascript/reference/math-atan-function-javascript.md)   
 [Funzione Math.cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Funzione Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Funzione Math.Tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Oggetto Math](../../javascript/reference/math-object-javascript.md)