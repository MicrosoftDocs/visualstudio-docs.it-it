---
title: Funzione debug. Write (JavaScript) | Documenti Microsoft
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
- Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugwrite-function-javascript"></a>Funzione Debug.write (JavaScript)
Invia le stringhe al debugger di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 *str1, str2,..., strN*  
 Parametro facoltativo. Stringhe da inviare al debugger di script.  
  
## <a name="remarks"></a>Note  
 Il `Debug.write` funzione invia stringhe alla finestra di controllo immediato di un debugger di script in fase di esecuzione. Se non viene eseguito il debug dello script, il `Debug.write` funzione non ha alcun effetto.  
  
 Il `Debug.write` è quasi identica alla funzione di `Debug.writeln` (funzione). L'unica differenza è che il `Debug.writeln` funzione Invia un carattere di nuova riga dopo le stringhe vengono inviate.  
  
## <a name="example"></a>Esempio  
 Questo esempio viene utilizzato il `Debug.write` funzione per visualizzare il valore della variabile nella finestra controllo immediato del debugger di script.  
  
> [!NOTE]
>  Per eseguire questo esempio, è necessario disporre di un debugger di script installato e deve eseguire lo script in modalità debug.  
>   
>  Internet Explorer 8 include le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] debugger. Se si usa una versione precedente di Internet Explorer, vedere [Procedura: Attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Debug (oggetto)](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)