---
title: Impossibile connettersi al processo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 15acb250c561cb1c7d414784f355a9239ead53ef
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="unable-to-attach-to-the-process"></a>Impossibile connettersi al processo
Impossibile connettersi al processo. Accesso negato per il componente del debugger che si trova sul server durante la connessione a questo computer.  
  
 Esistono due scenari comuni in cui viene generato questo errore:  
  
 **Scenario 1:** nel computer è in esecuzione Windows XP. Nel computer B è in esecuzione Windows Server 2003. Il Registro di sistema del computer B contiene il seguente valore DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 L'utente 1 avvia una sessione Terminal Server (sessione 1) sul computer B e avvia un'applicazione gestita da tale sessione.  
  
 L'utente 2, che è amministratore su entrambi i computer, è connesso al computer a Da qui, egli tenta di connettersi a un'applicazione in esecuzione nella sessione 1 sul computer B.  
  
 **Scenario 2:** un utente è connesso a due computer, A e B, nello stesso gruppo di lavoro, utilizzando la stessa password in entrambi i computer. Il debugger è in esecuzione sul computer e si tenta di connettersi a un'applicazione gestita in esecuzione sul computer b **l'accesso alla rete: modello di condivisione e sicurezza per gli account locali** impostato su **Guest**.  
  
### <a name="to-solve-scenario-1"></a>Per risolvere lo scenario 1  
  
-   Eseguire il debugger e l'applicazione gestita con lo stesso nome account e password.  
  
### <a name="to-solve-scenario-2"></a>Per risolvere lo Scenario 2  
  
1.  Dal **avviare** menu, scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo fare doppio clic su **strumenti di amministrazione**.  
  
3.  Nella finestra Strumenti di amministrazione, fare doppio clic su **criteri di sicurezza locali**.  
  
4.  Nella finestra Criteri di sicurezza locali selezionare **criteri locali**.  
  
5.  Nel **criteri** colonna, fare doppio clic su **l'accesso alla rete: modello di condivisione e sicurezza per gli account locali**.  
  
6.  Nel **l'accesso alla rete: modello di condivisione e sicurezza per gli account locali** finestra di dialogo, modificare l'impostazione di protezione locali per **classico**, fare clic su **OK**.  
  
    > [!CAUTION]
    >    L'impostazione del modello di sicurezza su Classico può determinare l'accesso imprevisto a file condivisi e componenti DCOM. In questo caso, un utente remoto può eseguire l'autenticazione con l'account utente locale anziché come Guest. Se il nome utente e la password specificati dall'utente remoto coincidono con quelli dell'account locale, tale utente potrà accedere a qualsiasi cartella o oggetto DCOM condiviso. Se si utilizza questo modello di sicurezza, assicurarsi che per tutti gli account utente sul computer siano impostate password complesse oppure configurare un'area di rete isolata per i computer coinvolti nelle operazioni di debug in modo da impedire l'accesso non autorizzato.  
  
7.  Chiudere tutte le finestre.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)