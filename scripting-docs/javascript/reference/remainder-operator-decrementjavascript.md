---
title: Resto (operatore) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="remainder-operator-javascript"></a>Operatore di resto (JavaScript)
Divide il valore di un'espressione per il valore di un altro e restituisce il resto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>Argomenti  
 `result`  
 Qualsiasi variabile.  
  
 `number1`  
 Qualsiasi espressione numerica.  
  
 `number2`  
 Qualsiasi espressione numerica.  
  
## <a name="remarks"></a>Note  
 L'operatore di resto divide `number1` da `number2`e restituisce solo il resto come `result`. Il segno di `result` è uguale al segno del `number1`. Il valore di `result` è compreso tra 0 e il valore assoluto di `number2`.  
  
 Il codice seguente viene illustrato come utilizzare l'operatore di resto.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
