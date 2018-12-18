---
title: Operatore di assegnazione di addizione (+ =) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>Operatore di assegnazione di addizione (+=) (JavaScript)
Aggiunge il valore di un'espressione a quello di una variabile e assegna il risultato alla variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression`  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Utilizzando questo operatore è esattamente lo stesso effetto: `result = result + expression`.  
  
 I tipi di due espressioni determinano il comportamento del `+=` operatore.  
  
|Se|Then|  
|--------|----------|  
|Entrambe le espressioni sono numerici o booleani|Aggiungi|  
|Entrambe le espressioni sono stringhe|Concatenare|  
|Un'espressione è di tipo numerica e l'altro è una stringa|Concatenare|  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore di addizione (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)