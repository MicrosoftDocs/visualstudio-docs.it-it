---
title: Funzione Math. hypot (JavaScript) | Documenti Microsoft
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathhypot-function-javascript"></a>Funzione Math.hypot (JavaScript)
Restituisce la radice quadrata della somma dei quadrati degli argomenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>Parametri  
 `value1`  
 Obbligatorio. Primo numero.  
  
 `value2`  
 Parametro facoltativo. Secondo numero.  
  
 `values`  
 Parametro facoltativo. Uno o più numeri.  
  
## <a name="remarks"></a>Note  
 Se un argomento è NaN, la funzione restituisce NaN. Se non vengono forniti argomenti, la funzione restituisce 0.  
  
## <a name="example"></a>Esempio  
 Di seguito è illustrato un esempio di uso della funzione `Math.hypot`.  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]