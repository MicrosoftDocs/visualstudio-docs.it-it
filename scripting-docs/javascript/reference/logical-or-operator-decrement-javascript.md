---
title: Logica o un operatore (|) (JavaScript) | Documenti Microsoft
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
- '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="logical-or-operator--javascript"></a>Operatore OR logico (||) (JavaScript)
Esegue una disgiunzione logica tra due espressioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>Parametri  
 *risultato*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Se una o entrambe le espressioni restituiscono **True**, *risultato* è **True**. Nella tabella seguente viene illustrato come *risultato* è determinato:  
  
|Se `expression1` è|E `expression2` è|Il `result` è|  
|-------------------------|--------------------------|---------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza le regole seguenti per la conversione di valori non booleani in valori booleani:  
  
-   Tutti gli oggetti sono considerati true.  
  
-   Le stringhe sono considerate false se e solo se sono vuote.  
  
-   `null`e non definite vengono considerate false.  
  
-   I numeri sono false se e solo se sono uguali a 0.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)