---
title: Eccezione generata e non rilevata | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>Eccezione generata e non rilevata
È incluso un `throw` istruzione nel codice, ma non è stato racchiuso tra parentesi una **provare** blocco, o è stato associato alcun **catch** blocco per intercettare l'errore. Le eccezioni vengono generate dall'interno il **provare** bloccato tramite il **generare** istruzione e rilevata di fuori di **provare** blocco con un **catch** istruzione.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Racchiudere il codice che può generare un'eccezione in un **provare** bloccare e verificare che sia presente un corrispondente **catch** blocco.  
  
-   Verificare che l'istruzione catch prevede il formato corretto dell'eccezione.  
  
-   Se l'eccezione viene generata nuovamente, assicurarsi che non è un'altra istruzione catch corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)   
 [Istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)