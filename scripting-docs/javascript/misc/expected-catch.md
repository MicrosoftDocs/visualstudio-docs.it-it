---
title: Previsto &#39; catch &#39; | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="expected-39catch39"></a>Previsto &#39; catch &#39;
È stata utilizzata la gestione delle eccezioni **provare** bloccata, ma non scritto personalmente associato **catch** istruzione. Il meccanismo di gestione delle eccezioni richiede che il codice può avere esito negativo, e il codice che non deve essere eseguita se si verifica un'eccezione, mandata a capo all'interno di un **provare** blocco. Le eccezioni vengono generate dall'interno il **provare** bloccato tramite il **generare** istruzione e rilevata di fuori di **provare** blocco con uno o più **catch**istruzioni.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere l'oggetto associato **catch** blocco.  
  
-   Provare a usare un **infine** anziché il blocco una **catch** blocco.  
  
## <a name="see-also"></a>Vedere anche  
 [try...... finally istruzione catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)