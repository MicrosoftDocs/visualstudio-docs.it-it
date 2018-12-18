---
title: Gli operatori di confronto (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>Operatori di confronto (JavaScript)
Restituisce un valore booleano che indica il risultato del confronto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>Parametri  
 `expression1`  
 Qualsiasi espressione.  
  
 `comparisonoperator`  
 Qualsiasi operatore di confronto.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Quando si confrontano stringhe, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore del carattere Unicode dell'espressione stringa.  
  
 Di seguito viene descritto il comportano di vari gruppi di operatori a seconda del tipo e valore di `expression1` e `expression2`:  
  
 Operatori relazionali: `<`, `>`, `<=`,`>=`  
  
-   Tenta di convertire entrambi `expression1` e `expression2` in numeri.  
  
-   Se entrambe le espressioni sono stringhe, eseguire un confronto tra stringhe.  
  
-   Se delle espressioni è `NaN`, restituito `false`.  
  
-   Zero negativo è uguale a zero positivo.  
  
-   Valore di infinito negativo è minore di tutto, incluso se stesso.  
  
-   Un numero infinito positivo è maggiore di tutto, incluso se stesso.  
  
 Gli operatori di uguaglianza: `==`,`!=`  
  
-   Se i tipi delle due espressioni sono diversi, provare a convertirli in una stringa, numero o valore booleano.  
  
-   `NaN`non è uguale a qualsiasi elemento incluso se stesso.  
  
-   Zero negativo è uguale a zero positivo.  
  
-   `null`è uguale a entrambi `null` e `undefined`.  
  
-   I valori sono considerati uguali se sono stringhe identiche, valori numerici equivalenti, l'oggetto stesso, valori booleani identici, o (se tipi diversi) può essere assegnati a una di queste situazioni.  
  
-   Qualsiasi altro confronto viene considerato diverso.  
  
 Operatori di identità: `===`,`!==`  
  
 Questi operatori si comportano come gli operatori di uguaglianza, ad eccezione del fatto che non viene eseguita alcuna conversione dei tipi. Se i tipi di entrambe le espressioni non sono uguali, queste espressioni restituiscono sempre `false`.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)