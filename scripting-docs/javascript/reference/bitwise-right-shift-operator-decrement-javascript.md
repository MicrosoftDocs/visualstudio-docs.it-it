---
title: Operatore di spostamento a destra bit per bit (&gt;&gt;) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>Operatore di spostamento a destra bit per bit (&gt;&gt;) (JavaScript)
Destra Sposta i bit di un'espressione, mantenendo il segno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Il >> operatore Sposta i bit di *expression1* destra del numero di bit specificato in *expression2*. Il bit del segno *expression1* viene utilizzato per riempire le cifre da sinistra. Vengono eliminate le cifre spostate a destra. Ad esempio, dopo il codice seguente viene valutato, *temp* ha un valore di -4:-14 (binario complemento 11110010 in due) spostato a destra di due bit uguale -4 (binario complemento 11111100 formato in due).  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Bit per bit operatore Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore di assegnazione di spostamento a destra (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operatore Right Shift senza segno (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)