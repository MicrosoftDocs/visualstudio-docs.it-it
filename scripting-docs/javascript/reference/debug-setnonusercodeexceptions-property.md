---
title: "Proprietà Debug setnonusercodeexceptions | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugsetnonusercodeexceptions-property"></a>Proprietà Debug.setNonUserCodeExceptions
Determina se tutti i blocchi try-catch in questo ambito sono considerati dal debugger come gestita dall'utente. Eccezioni possono essere classificate come generata, gestita dall'utente o non gestite.  
  
 Se questa proprietà è impostata su `true` in un determinato ambito, il debugger può determinare quindi eseguire un'azione (ad esempio, interruzione) nelle eccezioni generate all'interno di tale ambito, se lo sviluppatore desidera interrompere l'esecuzione in eccezioni non gestite dall'utente. Se questa proprietà è impostata su `false` è lo stesso come se la proprietà non è stata impostata.  
  
 Per ulteriori informazioni sul debug, vedere [Panoramica di debug Script ActiveX](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene mostrato come impostare questa proprietà.  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]