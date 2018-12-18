---
title: Operatore AND logico (&amp;&amp;) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="logical-and-operator-ampamp-javascript"></a>Operatore AND logico (&amp;&amp;) (JavaScript)
Esegue una congiunzione logica tra due espressioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## <a name="remarks"></a>Note  
 Se `expression1` viene valutato in `false`, `result` è `expression1`. In caso contrario, `result` sarà `expression2`. Di conseguenza, l'operazione restituisce `true` se entrambi gli operandi sono true; in caso contrario, verrà restituito `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza le regole seguenti per la conversione di valori non booleani in valori booleani:  
  
-   Tutti gli oggetti sono considerati `true`.  
  
-   Le stringhe sono considerate `false` se sono vuote.  
  
-   `null` e `undefined` sono considerati `false`.  
  
-   Un numero è `false` se è zero.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)