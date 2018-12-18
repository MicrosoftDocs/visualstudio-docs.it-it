---
title: Funzione Math. Round (JavaScript) | Documenti Microsoft
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
- round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Funzione Math.round (JavaScript)
Restituisce un'espressione numerica specificata, arrotondata all'intero più vicino.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `number` argomento è il valore da arrotondare all'intero più vicino.  
  
 Per i numeri positivi, se la parte decimale di `number` è 0,5 o maggiore, il valore restituito è uguale al valore integer più piccolo maggiore di `number`. Se la parte decimale è minore di 0,5, il valore restituito è l'intero massimo minore o uguale a `number`.  
  
 Per i numeri negativi, se la parte decimale è esattamente il valore restituito di -0,5, è l'intero più piccolo che è maggiore del numero.  
  
 Ad esempio, `Math.round(8.5)` restituisce 9, ma `Math.round(-8.5)` restituisce -8.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Math (oggetto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Math.random](../../javascript/reference/math-random-function-javascript.md)