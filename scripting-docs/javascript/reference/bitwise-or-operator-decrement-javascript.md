---
title: Bit per bit o un operatore (|) (JavaScript) | Documenti Microsoft
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
- '|'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, OR operator
- OR operator
- '| operator'
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a91c616c84b9d38154bf936f61fb856a4ebad0f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-operator--javascript"></a>Operatore OR bit per bit (|) (JavaScript)
Esegue un'operazione OR bit per bit su due espressioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 | expression2  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Il **&#124;** confrontata la rappresentazione binaria dei valori di due espressioni ed eseguita un'operazione OR bit per bit su di essi. Il risultato di questa operazione si comporta come segue:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Ogni volta che una delle espressioni con valore 1 nella stessa posizione, il risultato avrà 1 in tale cifra. In caso contrario, il risultato avrà il valore 0 in tale cifra.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Bit per bit o operatore di assegnazione (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)