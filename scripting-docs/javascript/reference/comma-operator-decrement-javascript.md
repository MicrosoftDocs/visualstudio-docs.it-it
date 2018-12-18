---
title: Operatore di valori delimitati da virgole (,) (JavaScript) | Documenti Microsoft
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
- '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="comma-operator--javascript"></a>Operatore virgola (,) (JavaScript)
In questo modo due espressioni vengono eseguite in sequenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>Parametri  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Il `,` operatore fa sì che le espressioni deve essere eseguito in ordine da sinistra a destra. Per un utilizzo comune di `,` è operatore nell'espressione di incremento di un `for` ciclo. Ad esempio:  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 Il `for` istruzione consente solo una singola espressione devono essere eseguiti alla fine di ogni iterazione di un ciclo. Il `,` operatore consente più espressioni di essere considerato come un'unica espressione, pertanto possono essere incrementate entrambe le variabili.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)