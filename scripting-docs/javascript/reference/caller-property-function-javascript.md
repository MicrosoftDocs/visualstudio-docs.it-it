---
title: "Proprietà caller (Function) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>Proprietà caller (Function) (JavaScript)
Ottiene la funzione che ha richiamato la funzione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>Note  
 Il `functionName` è in esecuzione il nome di qualsiasi funzione dell'oggetto.  
  
 Il `caller` proprietà definita per una funzione solo se si che è in esecuzione. Se la funzione viene chiamata dall'alto livello di un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] programma `caller` contiene `null`.  
  
 Se il `caller` proprietà viene utilizzata in un contesto di stringa, il risultato è identico `functionName`.`toString`, vale a dire, cui viene visualizzato il testo decompilato della funzione.  
  
 Nell'esempio seguente viene illustrato l'uso della proprietà `caller`:  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)