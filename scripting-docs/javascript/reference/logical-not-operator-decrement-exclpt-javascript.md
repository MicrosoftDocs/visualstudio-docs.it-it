---
title: Logico NOT (operatore) (!) (JavaScript) | Documenti Microsoft
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
- '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>Operatore di NOT logico (!) (JavaScript)
Esegue una negazione logica su un'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *espressione*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Nella tabella seguente viene illustrato come *risultato* è determinata.  
  
|Se `expression` è|Quindi `result` è|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 Tutti gli operatori unari, ad esempio il **!** operatore di valutare le espressioni come indicato di seguito:  
  
-   Se applicato undefined o `null` viene generato un errore di run-time espressioni.  
  
-   Gli oggetti vengono convertiti in stringhe.  
  
-   Le stringhe vengono convertite in numeri, se possibile. In caso contrario, viene generato un errore di run-time.  
  
-   I valori booleani vengono considerati come numeri (0 se è false, 1 se è true).  
  
 L'operatore viene applicato per il numero risultante.  
  
 Per il **!** operatore, se *espressione* è diverso da zero, *risultato* è zero. Se *espressione* è zero, *risultato* è 1.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Bit per bit NOT (operatore) (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)