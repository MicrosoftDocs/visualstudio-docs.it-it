---
title: Operatori di incremento (+ +) e decremento (-) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="increment--and-decrement----operators-javascript"></a>Operatori di incremento (++) e decremento (--) (JavaScript)
Gli incrementi di operatore di incremento e decrementa di operatore di decremento del valore di una variabile da uno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `variable`  
 Qualsiasi variabile.  
  
## <a name="remarks"></a>Note  
 Se l'operatore viene visualizzato prima variabile, il valore viene modificato prima della valutazione dell'espressione. Se l'operatore viene visualizzato dopo la variabile, il valore viene modificato dopo l'espressione viene valutata.  In altre parole, dato `j = ++k;`, il valore di `j` è il valore originale di `k` più uno; specificato `j = k++;`, il valore di `j` è il valore originale di `k`, che viene incrementato dopo che il relativo valore viene assegnato a `j`.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)