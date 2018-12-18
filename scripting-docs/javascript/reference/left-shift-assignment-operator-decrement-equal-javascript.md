---
title: Operatore di assegnazione di spostamento a sinistra (&lt;&lt;=) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- <<= operator [JavaScript]
- left shift assignment operator (<<=) [JavaScript]
- left shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00545947f6a84f99c519fcbed887b84c179fb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="left-shift-assignment-operator-ltlt-javascript"></a>Operatore di assegnazione di spostamento a sinistra (&lt;&lt;=) (JavaScript)
Sposta il numero specificato di bit a sinistra e assegna il risultato a `result`. I bit liberati dall'operazione di vengono riempiti con 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result <<= expression  
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression`  
 Il numero di bit da spostare.  
  
## <a name="remarks"></a>Note  
 Utilizzo di `<<=` operatore è lo stesso effetto`result = result << expression`  
  
 Nell'esempio seguente viene illustrato come utilizzare l'operatore `<<=`.  
  
```JavaScript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Bit per bit operatore Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore di spostamento a destra bit per bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift senza segno (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)