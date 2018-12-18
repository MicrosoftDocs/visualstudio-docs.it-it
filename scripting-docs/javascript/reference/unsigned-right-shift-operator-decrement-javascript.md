---
title: Operatore Right Shift senza segno (&gt;&gt;&gt;) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>Operatore Right Shift senza segno (&gt;&gt;&gt;) (JavaScript)
Destra Sposta i bit di un'espressione, ignorando il segno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Il  **>>>**  operatore Sposta i bit di *expression1* destra del numero di bit specificato in *expression2*. Gli zeri vengono compilati da sinistra. Vengono eliminate le cifre spostate a destra. Ad esempio:  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 La variabile *temp* ha un valore iniziale di -14 (11111111 11111111 11111111 11110010 in formato binario complemento a due). Quando si tratta di uno spostamento a destra due bit, il valore è uguale a 1073741820 (00111111 11111111 11111111 11111100 in formato binario).  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore di assegnazione Right Shift senza segno (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Bit per bit operatore Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore di spostamento a destra bit per bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)