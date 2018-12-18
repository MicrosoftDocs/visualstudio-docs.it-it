---
title: non definito (costante) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>Costante undefined (JavaScript)
Un valore che non è stata mai definito, ad esempio una variabile che non è stata inizializzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
undefined  
```  
  
## <a name="remarks"></a>Note  
 Il `undefined` costante è un membro del `Global` dell'oggetto e diventa disponibile quando viene inizializzato il motore di script. Quando una variabile dichiarata ma non inizializzata, il valore è **definito**.  
  
 Se non è stata dichiarata una variabile, non è possibile confrontare a `undefined`, ma è possibile confrontare il tipo della variabile in cui la stringa "undefined".  
  
 Il `undefined` costante è utile quando in modo esplicito di test o impostare una variabile non definita.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `undefined` costante.  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>Requisiti  
 Il `undefined` proprietà è stata introdotta in [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]ed è stato eseguito in sola lettura [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)