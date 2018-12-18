---
title: 'Errore: Errore di accesso remoto del gruppo di lavoro | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38ec2de37279e1f383751c9652aeeac74473c50f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-workgroup-remote-logon-failure"></a>Errore: accesso remoto al gruppo di lavoro non riuscito
Il testo del messaggio di errore è il seguente:  
  
 Accesso non riuscito: nome utente sconosciuto o password errata.  
  
 **Causa**  
  
 Questo errore può verificarsi quando si esegue il debug da un computer che fa parte di un gruppo di lavoro e si tenta di stabilire la connessione a un computer remoto. Fra le cause possibili vi sono le seguenti:  
  
-   Nel computer remoto non esiste un account con il nome e la password specificati.  
  
-   Se il computer di Visual Studio e il computer remoto sono gruppi di lavoro, questo errore può verificarsi a causa del valore predefinito **criteri di sicurezza locali** impostazione sul computer remoto. L'impostazione predefinita per il **criteri di sicurezza locali** impostazione **solo Guest: gli utenti locali effettuano l'autenticazione come Guest**. Per eseguire il debug con questa configurazione, è necessario modificare l'impostazione del computer remoto in **classico: gli utenti locali effettuano l'autenticazione come stessi**.  
  
> [!NOTE]
>  Per effettuare le attività elencate di seguito è necessario disporre di diritti amministrativi.  
  
### <a name="to-open-the-local-security-policy-window"></a>Per aprire la finestra Criteri di sicurezza locali  
  
1.  Avviare il **secpol.msc** snap-in Microsoft Management Console. Digitare secpol.msc nella funzionalità di ricerca di Windows, nella casella Esegui di Windows o a un prompt dei comandi.  
  
### <a name="to-add-user-rights-assignments"></a>Per aggiungere assegnazioni di diritti utente  
  
1.  Aprire il **criteri di sicurezza locali** finestra.  
  
2.  Espandere il **criteri locali** cartella.  
  
3.  Fare clic su **Assegnazione diritti utente**.  
  
4.  Nel **criteri** colonna, fare doppio clic su **il Debug di programmi** per visualizzare le assegnazioni di criteri di gruppo locale corrente nel **impostazioni di criteri di sicurezza locali** la finestra di dialogo.  
  
     ![Diritti utente criteri di sicurezza locali](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
5.  Per aggiungere nuovi utenti, fare clic su di **Aggiungi utente o gruppo** pulsante.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Per modificare il modello di condivisione e sicurezza  
  
1.  Aprire il **criteri di sicurezza locali** finestra.  
  
2.  Espandere il **criteri locali** cartella.  
  
3.  Fare clic su **opzioni di sicurezza**.  
  
4.  Nel **criteri** colonna, fare doppio clic su **l'accesso alla rete: modello di condivisione e sicurezza per gli account locali**.  
  
5.  Nel **l'accesso alla rete: modello di condivisione e sicurezza per gli account locali** finestra di dialogo, modificare il valore di **classico: gli utenti locali di autenticarsi con il proprio** e fare clic sul **applica**pulsante.  
  
     ![Opzioni di sicurezza Criteri di sicurezza locali](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)