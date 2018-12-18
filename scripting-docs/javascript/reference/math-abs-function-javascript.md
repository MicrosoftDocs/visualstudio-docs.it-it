---
title: Funzione Math.Abs (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathabs-function-javascript"></a>Funzione Math.abs (JavaScript)
Restituisce il valore assoluto di un numero (il valore senza considerare se è positivo o negativo). Ad esempio, il valore assoluto di -5 è lo stesso come il valore assoluto di 5.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>Parametri  
 Obbligatorio `number` argomento è un'espressione numerica per cui è necessario il valore assoluto.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore assoluto del `number` argomento.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `abs`.  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Math (oggetto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Math](../../javascript/reference/math-object-javascript.md)