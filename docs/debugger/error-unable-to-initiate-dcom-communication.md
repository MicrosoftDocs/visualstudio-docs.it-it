---
title: 'Errore: Impossibile avviare la comunicazione DCOM | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c34de251125b49c8b3d7aebf301468b9b1d0252a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Errore: impossibile avviare la comunicazione DCOM
Si è verificato un errore DCOM quando il computer locale ha tentato di comunicare con il computer remoto. Questo errore è causato dalla presenza di un firewall nel server remoto oppure dall'interruzione dell'autenticazione di Windows nel computer remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Se il computer remoto è abilitato Windows Firewall, vedere [il debug remoto](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.  
  
-   Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)