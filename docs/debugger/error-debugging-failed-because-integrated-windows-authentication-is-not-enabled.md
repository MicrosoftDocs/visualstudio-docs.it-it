---
title: "Errore: Il debug non è riuscita perché non è abilitata l'autenticazione integrata di Windows | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords: debugger, Web application errors
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d3d66a2892378f04061907e383965c6c02096bf1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Errore: debug non riuscito. Non è attivata l'autenticazione di Windows integrata
L'autenticazione dell'utente che ha richiesto il debug non è stata possibile a causa di un errore di autenticazione. Questo errore può verificarsi quando si tenta di eseguire un'applicazione Web o un servizio Web XML. Una causa di questo errore è la mancata attivazione dell'autenticazione di Windows integrata. Per attivarla, seguire i passaggi della procedura relativa all'attivazione dell'autenticazione integrata di Windows.  
  
 Se è stata abilitata l'autenticazione integrata di Windows e l'errore si ripete, è possibile che questo errore è dovuto **all'attivazione dell'autenticazione del Digest per i server di dominio Windows** è abilitata. In questa situazione è necessario consultare l'amministratore di rete.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Per attivare l'autenticazione di Windows integrata  
  
1.  Accedere al server Web mediante un account amministratore.  
  
2.  Fare clic su **avviare** e quindi fare clic su **Pannello di controllo**.  
  
3.  In **Pannello di controllo**, fare doppio clic su **strumenti di amministrazione**.  
  
4.  Fare doppio clic su **Internet Information Services**.  
  
5.  Fare clic sul nodo del server Web.  
  
     Oggetto **siti Web** verrà visualizzata la cartella sotto il nome del server.  
  
6.  È possibile configurare l'autenticazione per tutti i siti Web complessivamente o singolarmente. Per configurare l'autenticazione per tutti i siti Web, fare doppio clic su di **siti Web** cartella e quindi fare clic su **proprietà**. Per configurare l'autenticazione per un singolo sito Web, aprire il **siti Web** cartella, fare doppio clic su singolo sito Web e quindi fare clic su **proprietà**.  
  
     Il **proprietà** viene visualizzata la finestra di dialogo.  
  
7.  Fare clic su di **protezione Directory** scheda.  
  
8.  Nel **controllo autenticazione e accesso anonimo** fare clic su **modifica**.  
  
     Il **metodi di autenticazione** viene visualizzata la finestra di dialogo.  
  
9. In **accesso autenticato**selezionare **autenticazione integrata di Windows**.  
  
10. Fare clic su **OK** per chiudere la **metodi di autenticazione** la finestra di dialogo.  
  
11. Fare clic su **OK** per chiudere la **proprietà** la finestra di dialogo.  
  
12. Chiudi il **Internet Information Services** finestra.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Per attivare l'autenticazione integrata di Windows in Windows Vista/IIS 7  
  
1.  Accedere al server Web mediante un account amministratore.  
  
2.  Attivare Autenticazione di Windows e Compatibilità di gestione con IIS 6, se tale operazione non è stata già effettuata, seguendo questi passaggi:  
  
    1.  Fare clic su **avviare**, fare clic su **Pannello di controllo** e quindi fare clic su **programmi**.  
  
    2.  In **programmi e funzionalità**, fare clic su **o disattivazione delle funzionalità Windows attivare**.  
  
         Verrà visualizzata la finestra di dialogo Controllo di accesso utente e verrà richiesto di immettere l'autorizzazione per continuare.  
  
    3.  Scegliere **Continua**.  
  
         Verrà visualizzata la finestra di dialogo Funzionalità Windows.  
  
    4.  Nell'elenco delle funzionalità espandere il **Internet Information Services** nodo.  
  
    5.  In **Internet Information Services**, espandere il **servizi World Wide Web** nodo.  
  
    6.  In **servizi World Wide Web**, fare clic su **sicurezza**.  
  
    7.  Fare clic su **l'autenticazione di Windows**.  
  
    8.  In **Internet Information Services**, espandere il **strumenti di gestione Web** nodo.  
  
    9. In **strumenti di gestione Web**, espandere il **compatibilità Gestione IIS 6** nodo e selezionare il **IIS 6 Metabase and IIS 6 Configuration Compatibility** casella di controllo.  
  
    10. In **strumenti di gestione Web**selezionare **Console di gestione IIS** e fare clic su **OK.**  
  
    11. Per rendere effettive queste modifiche, riavviare il computer.  
  
3.  Fare clic su **avviare** e quindi fare clic su **Pannello di controllo**.  
  
4.  Fare clic su **visualizzazione classica**, quindi fare doppio clic su **strumenti di amministrazione**.  
  
5.  Nel **nome** colonna e fare doppio clic su **Gestione Internet Information Services (IIS)**.  
  
6.  Nel **connessioni** colonna, espandere il nodo per il server.  
  
     Oggetto **siti Web** verrà visualizzata la cartella sotto il nome del server.  
  
7.  Espandere il **siti Web** nodo e fare clic sul sito Web per cui si desidera abilitare l'autenticazione integrata di Windows.  
  
8.  Il titolo del riquadro centrale viene sostituito con il nome del sito Web selezionato. In questo riquadro, sotto il **IIS** titolo, fare doppio clic su **autenticazione**.  
  
     Il titolo del riquadro viene sostituito con **autenticazione**.  
  
9. Nel **autenticazione** riquadro, nel **nome** colonna, fare doppio clic su **l'autenticazione di Windows** e quindi fare clic su **abilitare**.  
  
10. Chiudi il **Gestione Internet Information Services (IIS)** finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Autenticazione del Digest di Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Esecuzione di applicazioni in Windows Vista con IIS 7.0 e Visual Studio](http://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)