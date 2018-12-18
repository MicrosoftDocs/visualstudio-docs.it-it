---
title: Operatore di spostamento a sinistra bit per bit (&lt;&lt;) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>Operatore di spostamento a sinistra bit per bit (&lt;&lt;) (JavaScript)
Sinistra sposta i bit di un'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Il  **<<**  operatore Sposta i bit di *expression1* verso sinistra del numero di bit specificato in *expression2*. Ad esempio:  
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 La variabile *temp* ha un valore pari a 56 perché 14 (00001110 in formato binario) spostato a sinistra di due bit uguale a 56 (00111000 in formato binario).  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore di assegnazione di spostamento a sinistra (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operatore di spostamento a destra bit per bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift senza segno (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)