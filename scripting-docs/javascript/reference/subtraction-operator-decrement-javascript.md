---
title: Operatore di sottrazione (-) (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>Operatore di sottrazione (-) (JavaScript)
Sottrae il valore di un'espressione da un altro oppure di negazione unaria di un'unica espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile di tipo numerico.  
  
 `number`  
 Qualsiasi espressione numerica.  
  
 `number1`  
 Qualsiasi espressione numerica.  
  
 `number2`  
 Qualsiasi espressione numerica.  
  
## <a name="remarks"></a>Note  
 Nella sintassi 1, il  **-**  operatore è l'operatore di sottrazione aritmetica usato per calcolare la differenza tra due numeri. Nella sintassi 2, il  **-**  operatore viene utilizzato l'operatore di negazione unario per indicare il valore negativo di un'espressione.  
  
 Sintassi 2, come per tutti gli operatori unari, le espressioni vengono valutate come segue:  
  
-   Se applicato undefined o `null` viene generato un errore di run-time espressioni.  
  
-   Gli oggetti vengono convertiti in stringhe.  
  
-   Le stringhe vengono convertite in numeri, se possibile. In caso contrario, viene generato un errore di run-time.  
  
-   I valori booleani vengono considerati come numeri (0 se è false, 1 se è true).  
  
 L'operatore viene applicato per il numero risultante. Nella sintassi 2, se il numero risulta è diverso da zero, *risultato* è uguale al numero risultante con il segno opposto. Se il numero risulta è uguale a zero, *risultato* è zero.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore di assegnazione di sottrazione (-)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)