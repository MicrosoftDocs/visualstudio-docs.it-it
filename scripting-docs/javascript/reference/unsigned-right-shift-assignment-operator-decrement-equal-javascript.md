---
title: Operatore di assegnazione Right Shift senza segno (&gt;&gt;&gt;=) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>Operatore di assegnazione Right Shift senza segno (&gt;&gt;&gt;=) (JavaScript)
Sposta a destra il valore di una variabile per il numero di bit specificato nel valore di un'espressione, senza mantenere il segno, e assegna il risultato alla variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *espressione*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Utilizzo di >>> = operatore è esattamente come le operazioni seguenti:  
  
```JavaScript  
result = result >>> expression  
```  
  
 Il  **>>>=**  operatore Sposta i bit di *risultato* destra del numero di bit specificato in *espressione*. Gli zeri vengono compilati da sinistra. Vengono eliminate le cifre spostate a destra. Ad esempio:  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 La variabile *temp* ha un valore iniziale di -14 (11111111 11111111 11111111 11110010 in formato binario complemento a due). Dopo lo spostamento a destra i bit di due, il valore è uguale a 1073741820 (00111111 11111111 11111111 11111100 in formato binario).  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore Right Shift senza segno (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Bit per bit operatore Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore di spostamento a destra bit per bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)