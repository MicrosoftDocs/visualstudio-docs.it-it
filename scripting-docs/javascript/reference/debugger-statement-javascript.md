---
title: il debugger di istruzione (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugger-statement-javascript"></a>Istruzione debugger (JavaScript)
Sospende l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
debugger  
```  
  
## <a name="remarks"></a>Note  
 È possibile inserire `debugger` istruzioni in un punto qualsiasi nelle procedure per sospendere l'esecuzione. Utilizzo di `debugger` istruzione è simile all'impostazione di un punto di interruzione nel codice.  
  
 Il `debugger` istruzione sospende l'esecuzione, ma non chiudere qualsiasi file o deselezionare tutte le variabili.  
  
> [!NOTE]
>  Il `debugger` istruzione non ha alcun effetto a meno che lo script viene eseguito il debug.  
  
## <a name="example"></a>Esempio  
 Questo esempio viene utilizzato il `debugger` istruzione per sospendere l'esecuzione per ogni iterazione di `for` ciclo.  
  
> [!NOTE]
>  Per eseguire questo esempio, è necessario disporre di un debugger di script installato e deve eseguire lo script in modalità debug.  
>   
>  Internet Explorer 8 include le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] debugger. Se si usa una versione precedente di Internet Explorer, vedere [Procedura: Attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni JavaScript](../../javascript/reference/javascript-statements.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)