---
title: "0... n (proprietà) (argomenti) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="0n-properties-arguments-javascript"></a>Proprietà 0...n (arguments) (JavaScript)
Restituisce il valore effettivo di singoli argomenti da un **argomenti** oggetto restituito dal **argomenti** proprietà di una funzione in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>Parametri  
 *function*  
 Parametro facoltativo. Il nome di attualmente in esecuzione `Function` oggetto.  
  
 0, 1, 2, *, n*  
 Obbligatorio. Valore intero non negativo compreso nell'intervallo compreso tra 0 e  *n*  dove 0 rappresenta il primo argomento e  *n*  rappresenta l'argomento finale. Il valore dell'argomento finale  *n*  è **arguments. Length-1**.  
  
## <a name="remarks"></a>Note  
 I valori restituiti da 0. . . n proprietà sono i valori effettivi passati alla funzione in esecuzione. Mentre non è effettivamente una matrice di argomenti, ai singoli argomenti che costituiscono il **argomenti** oggetto accessibili nello stesso modo che gli elementi della matrice sono accede.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **0...**  ***n***proprietà del **argomenti** oggetto. Per comprendere meglio l'esempio, passare uno o più argomenti alla funzione:  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Funzione oggetto](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà length (arguments)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Proprietà length (Function)](../../javascript/reference/length-property-function-javascript.md)