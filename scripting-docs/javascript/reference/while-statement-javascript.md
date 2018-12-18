---
title: while (istruzione) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="while-statement-javascript"></a>Istruzione while (JavaScript)
Esegue un'istruzione o serie di istruzioni finché una condizione specificata è `false`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parametri  
 `expression`  
 Obbligatorio. Un'espressione booleana che viene verificata prima di ogni iterazione del ciclo. Se `expression` è `true`, l'esecuzione del ciclo. Se `expression` è `false`, il ciclo viene interrotto.  
  
 `statements`  
 Parametro facoltativo. Una o più istruzioni da eseguire se `expression` è `true`.  
  
## <a name="remarks"></a>Note  
 Il `while` controlli istruzione `expression` prima dell'esecuzione di un ciclo. Se `expression` è `false` a questo punto, il ciclo non è mai eseguito.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `while`.  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)   
 [Istruzione Do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)