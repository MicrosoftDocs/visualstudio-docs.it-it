---
title: "Proprietà length (Function) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-function-javascript"></a>Proprietà length (Function) (JavaScript)
Ottiene il numero di argomenti definiti per una funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio *functionName* è il nome della funzione.  
  
 Il **lunghezza** proprietà di una funzione viene inizializzata dal motore di scripting per il numero di argomenti nella definizione della funzione quando viene creata un'istanza della funzione.  
  
 Cosa accade quando viene chiamata una funzione con un numero di argomenti diverso dal valore del relativo **lunghezza** proprietà dipende dalla funzione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **lunghezza** proprietà:  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Arguments (Function)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Proprietà length (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [Proprietà length (String)](../../javascript/reference/length-property-string-javascript.md)