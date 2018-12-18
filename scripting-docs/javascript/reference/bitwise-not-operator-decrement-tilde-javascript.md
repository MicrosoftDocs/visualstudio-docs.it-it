---
title: Bit per bit NOT (operatore) (~) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ~
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-not-operator--javascript"></a>Operatore NOT bit per bit (~) (JavaScript)
Esegue un'operazione NOT bit per bit (negazione) su un'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *espressione*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Tutti gli operatori unari, ad esempio il `~` operatore, valutare le espressioni come indicato di seguito:  
  
-   Se applicato undefined o `null` viene generato un errore di run-time espressioni.  
  
-   Gli oggetti vengono convertiti in stringhe.  
  
-   Le stringhe vengono convertite in numeri, se possibile. In caso contrario, viene generato un errore di run-time.  
  
-   I valori booleani vengono considerati come numeri (0 se è false, 1 se è true).  
  
 L'operatore viene applicato per il numero risultante.  
  
 Il `~` confrontata la rappresentazione binaria dei valori dell'espressione ed eseguita un'operazione di negazione bit per bit su di esso.  
  
 Qualsiasi cifra che corrisponde a 1 dell'espressione diventa 0 nel risultato. Le cifre che corrisponde a 0 nell'espressione diventano un 1 nel risultato.  
  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo di bit per bit (~) l'operatore NOT.  
  
```  
var temp = ~5;  
```  
  
 Il valore risultante è -6, come illustrato nella tabella seguente.  
  
|Espressione|Valore binario (complemento a due)|Valore decimale|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Logico NOT (operatore) (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)