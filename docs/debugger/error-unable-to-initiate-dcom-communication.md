---
title: 'Errore: Impossibile avviare la comunicazione DCOM | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4aead8cd4396df540779fdeebec953859122fd47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Errore: impossibile avviare la comunicazione DCOM
Si è verificato un errore DCOM quando il computer locale ha tentato di comunicare con il computer remoto. Questo errore è causato dalla presenza di un firewall nel server remoto oppure dall'interruzione dell'autenticazione di Windows nel computer remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Se il computer remoto è abilitato Windows Firewall, vedere [il debug remoto](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.  
  
-   Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)