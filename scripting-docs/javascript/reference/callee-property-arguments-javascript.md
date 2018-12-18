---
title: "Proprietà callee (arguments) (JavaScript) | Documenti Microsoft"
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
- callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="callee-property-arguments-javascript"></a>Proprietà callee (arguments) (JavaScript)
Restituisce il `Function` oggetto in esecuzione, vale a dire, il testo del corpo dell'oggetto specificato `Function` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>Note  
 Facoltativo *funzione* argomento è il nome di attualmente in esecuzione `Function` oggetto.  
  
 Il `callee` proprietà è un membro del **argomenti** oggetto che diventa disponibile solo quando la funzione associata è in esecuzione.  
  
 Il valore iniziale del `callee` proprietà è il `Function` dell'oggetto in esecuzione. In questo modo funzioni anonime sono ricorsivi.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Funzione oggetto](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà caller (Function)](../../javascript/reference/caller-property-function-javascript.md)