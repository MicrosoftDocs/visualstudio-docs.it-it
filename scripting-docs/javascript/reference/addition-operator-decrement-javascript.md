---
title: Operatore di addizione (+) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>Operatore di addizione (+) (JavaScript)
Aggiunge il valore di un'espressione numerica a un'altra o concatena due stringhe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 I tipi di due espressioni determinano il comportamento del  **+**  operatore.  
  
|Se|Then|  
|--------|----------|  
|Entrambe le espressioni sono numerici o booleani|Aggiungi|  
|Entrambe le espressioni sono stringhe|Concatenare|  
|Un'espressione è di tipo numerica e l'altro è una stringa|Concatenare|  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore di assegnazione di addizione (+ =)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)