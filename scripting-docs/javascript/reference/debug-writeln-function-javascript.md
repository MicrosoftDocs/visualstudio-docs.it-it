---
title: Funzione debug. writeln (JavaScript) | Documenti Microsoft
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
- writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugwriteln-function-javascript"></a>Funzione Debug.writeln (JavaScript)
Invia le stringhe al debugger di script, seguito da un carattere di nuova riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 *str1, str2,..., strN*  
 Parametro facoltativo. Stringhe da inviare al debugger di script.  
  
## <a name="remarks"></a>Note  
 Il `Debug.writeln` funzione invia stringhe, seguite da un carattere di nuova riga, la finestra di controllo immediato di Microsoft Script Debugger in fase di esecuzione. Se non viene eseguito il debug dello script, il `Debug.writeln` funzione non ha alcun effetto.  
  
 Il `Debug.writeln` è quasi identica alla funzione di `Debug.write` (funzione). L'unica differenza è che il `Debug.write` funzione non invia un carattere di nuova riga dopo l'invio di stringhe.  
  
## <a name="example"></a>Esempio  
 Questo esempio viene utilizzato il `Debug.writeln` funzione per visualizzare il valore della variabile nella finestra controllo immediato di Microsoft Script Debugger.  
  
> [!NOTE]
>  Per eseguire questo esempio, è necessario disporre di un debugger di script installato e deve eseguire lo script in modalità debug.  
>   
>  Internet Explorer 8 include le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] debugger. Se si usa una versione precedente di Internet Explorer, vedere [Procedura: Attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Debug (oggetto)](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Debug.write](../../javascript/reference/debug-write-function-javascript.md)