---
title: Operatore di assegnazione di spostamento a destra (&gt;&gt;=) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>Operatore di assegnazione di spostamento a destra (&gt;&gt;=) (JavaScript)
Sposta a destra il valore di una variabile per il numero di bit specificato nel valore di un'espressione, mantenendo il segno, e assegna il risultato alla variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *espressione*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Utilizzo di  **>>=**  operatore è lo stesso effetto:  
  
```JavaScript  
result = result >> expression  
```  
  
 Il  **>>=**  operatore Sposta i bit di *risultato* destra del numero di bit specificato in *espressione*. Il bit del segno *risultato* viene utilizzato per riempire le cifre da sinistra. Vengono eliminate le cifre spostate a destra. Ad esempio, dopo il codice seguente viene valutato, *temp* ha un valore di -4: 14 (11110010 in formato binario) spostato a destra di due bit uguale -4 (11111100 in formato binario).  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Bit per bit operatore Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore di spostamento a destra bit per bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift senza segno (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)