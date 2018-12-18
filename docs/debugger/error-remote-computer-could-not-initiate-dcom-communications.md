---
title: "Errore: Il computer remoto non è possibile avviare le comunicazioni DCOM | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bdd235db0473a956a57d6d6093b5149bac76d3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Errore: il computer remoto non può avviare le comunicazioni DCOM
Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM. Il computer locale è il computer che  
  
 esegue Visual Studio. L'errore può essere determinato da numerose cause:  
  
-   Nel computer locale è stato attivato un firewall.  
  
-   L'autenticazione di Windows dal computer remoto al computer locale non funziona.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Se nel computer locale è abilitato Windows Firewall, vedere [il debug remoto](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.  
  
2.  Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.  
  
3.  Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)