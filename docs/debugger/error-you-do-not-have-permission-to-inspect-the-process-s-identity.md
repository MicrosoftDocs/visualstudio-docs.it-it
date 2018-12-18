---
title: "Errore: Non si dispone dell'autorizzazione per controllare il processo di &#39; identità s | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f51087d4f7882c34826942a898328640107a5ac6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Errore: Non si dispone dell'autorizzazione per controllare il processo di &#39; identità s
Non si dispone dell'autorizzazione necessaria per controllare l'identità del processo. Probabilmente l'errore è causato dalla configurazione del sistema.  
  
 Il debugger non è stato in grado di controllare l'identità del processo, un'informazione necessaria per l'esecuzione del debug. Probabilmente Servizi terminal è disabilitato. Per impostazione predefinita, questo servizio è attivato. Per riattivarlo, eseguire la procedura seguente.  
  
### <a name="to-enable-terminal-services"></a>Per attivare Servizi terminal  
  
1.  Fare clic su **avviare** e quindi scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo, scegliere **passa alla visualizzazione classica**, se necessario, quindi fare doppio clic su **strumenti di amministrazione**.  
  
3.  Nel **strumenti di amministrazione** finestra, fare doppio clic su **Gestione Computer**.  
  
4.  Nella finestra Gestione Computer espandere il **servizi e applicazioni** nodo.  
  
5.  Sotto il **servizi e applicazioni**, fare clic su **servizi**.  
  
     Nel riquadro di destra verrà visualizzato un elenco di servizi.  
  
6.  Nel **servizi** elenco, fare doppio clic su **servizi Terminal** e quindi scegliere **proprietà**.  
  
7.  Nel **proprietà servizi Terminal** finestra, passa al **generale** scheda e impostare **tipo di avvio** a **manuale**.  
  
8.  Fare clic su **OK**.  
  
9. Riavviare il computer.  
  
     Con questa procedura non si attiva automaticamente Desktop remoto. Se si desidera attivare Desktop remoto nel computer in uso, eseguire la procedura aggiuntiva seguente.  
  
### <a name="to-enable-remote-desktop"></a>Per attivare Desktop remoto  
  
1.  Fare clic su **avviare** e quindi fare doppio clic su **risorse del Computer**.  
  
2.  Scegliere **proprietà**.  
  
     Il **le proprietà di sistema** verrà visualizzata la finestra.  
  
3.  Fare clic su **remoto**.  
  
4.  In **Desktop remoto**selezionare **consentire agli utenti di connettersi in remoto al computer**.  
  
5.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)