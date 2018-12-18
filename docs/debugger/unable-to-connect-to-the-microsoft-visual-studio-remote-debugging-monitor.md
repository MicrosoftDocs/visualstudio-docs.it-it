---
title: Impossibile connettersi a Microsoft Visual Studio Remote Debugging Monitor | Documenti Microsoft
ms.custom: 
ms.date: 08/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
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
ms.openlocfilehash: 6efbb27052dc837ab10a74d8f43e949dfb816190
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Impossibile eseguire la connessione a Microsoft Visual Studio Remote Debugging Monitor
Questo messaggio può verificarsi perché remote debugging monitor non è configurato correttamente nel computer remoto o il computer remoto sia accessibile a causa di problemi di rete o la presenza di un firewall.
  
> [!IMPORTANT]
>  Se si ritiene di aver ricevuto questo messaggio a causa di un bug del prodotto, [segnalare il problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) a Visual Studio. Per ottenere ulteriore assistenza, vedere [Talk to Us](../ide/talk-to-us.md) per le modalità di contatto di Microsoft.

## <a name="specificerrors"></a>Che cos'è il messaggio di errore dettagliato?

Il `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` messaggio è di tipo generico. In genere, un messaggio più specifico è incluso nella stringa di errore e che consentono di identificare la causa del problema o cercare una correzione più precisa. Ecco alcuni dei messaggi di errore più comuni che vengono aggiunti al messaggio di errore principale:

- [Il debugger non può connettersi al computer remoto. Il debugger non è riuscito a risolvere il nome del computer specificato](#cannot_connect)
- [Richiesta di connessione è stata rifiutata dal debugger remoto](#rejected)
- [Accesso non valido alla posizione di memoria](#invalid_access)
- [Non è presente alcun server con il nome specificato in esecuzione nel computer remoto](#no_server)
- [Il nome richiesto è valido, ma nessun dato del tipo richiesto è stato trovato](#valid_name)
- [Visual Studio Remote Debugger nel computer di destinazione non è possibile connettersi a questo computer](#cant_connect_back)
- [Accesso negato](#access_denied)
- [Si è verificato un errore specifico del pacchetto di sicurezza](#security_package)

## <a name="cannot_connect"></a>Il debugger non può connettersi al computer remoto. Il debugger non è riuscito a risolvere il nome del computer specificato

Provare questi passaggi:

1. Assicurarsi di immettere un nome computer valido e numero di porta di **Connetti a processo** la finestra di dialogo o nelle proprietà del progetto (per impostare le proprietà, vedere [procedura](#server_incorrect)). Il nome del computer deve essere il seguente formato:

    `computername:port`

    > [!NOTE]
    > Il numero di porta deve corrispondere il [numero del debugger remoto porta](../debugger/remote-debugger-port-assignments.md), quali *deve essere in esecuzione* nel computer di destinazione.

2. Se il nome del computer non funziona, provare l'indirizzo IP e numero della porta.

3. Assicurarsi che la versione del debugger remoto in esecuzione nel computer di destinazione corrisponde alla versione di Visual Studio. Per ottenere la versione corretta del debugger remoto, vedere [il debug remoto](../debugger/remote-debugging.md).

    > [!TIP]
    > Se si collega al processo e si connetta correttamente ma non viene visualizzato il processo di cui si desidera, selezionare il **Mostra i processi di casella di controllo di tutti gli utenti**. I processi verranno visualizzati se si è connessi con un account utente diverso.

4. Se l'errore persiste, vedere [il computer remoto non è raggiungibile](#dns).

## <a name="rejected"></a>Richiesta di connessione è stata rifiutata dal debugger remoto

Nel **Connetti a processo** finestra di dialogo casella o nelle proprietà del progetto, verificare che il nome del computer remoto e il numero di porta corrisponda al numero di porta e nome visualizzato nella finestra del debugger remoto. Se non sono corrette, correggere e riprovare.

Se questi valori siano corretti e che il messaggio indica **l'autenticazione di Windows** modalità, verificare che il debugger remoto sia in modalità di autenticazione corretta (**strumenti > Opzioni**).

## <a name="invalid_access"></a>Accesso non valido alla posizione di memoria

Si è verificato un errore interno. Riavviare Visual Studio e riprovare.

## <a name="no_server"></a>Non è presente alcun server con il nome specificato in esecuzione nel computer remoto

Impossibile connettersi al debugger remoto di Visual Studio. Questo messaggio può verificarsi per diversi motivi:

- Il debugger remoto può essere eseguito con un account utente diverso. Vedere [questi passaggi](#user_accounts)

- La porta è bloccata nel firewall. Assicurarsi che il firewall sia [non stia bloccando la richiesta](#firewall), soprattutto se si utilizza un firewall di terze parti.

- La versione del debugger remoto non corrisponde a Visual Studio. Per ottenere la versione corretta del debugger remoto, vedere [debug remoto](../debugger/remote-debugging.md)


## <a name="#valid_name"></a>Il nome richiesto è valido, ma nessun dato del tipo richiesto è stato trovato

È presente nel computer remoto, ma Impossibile connettersi al debugger remoto di Visual Studio. Questo messaggio può verificarsi per diversi motivi:

- Un problema DNS impedisce la connessione. Vedere [procedura](#dns).

- Il debugger remoto può essere eseguito con un account utente diverso. Seguire [procedura](#user_accounts).

- La porta è bloccata nel firewall. Assicurarsi che il firewall sia [non stia bloccando la richiesta](#firewall), soprattutto se si utilizza un firewall di terze parti.

- La versione del debugger remoto non corrisponde a Visual Studio. Per ottenere la versione corretta del debugger remoto, vedere [il debug remoto](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a>Visual Studio Remote Debugger nel computer di destinazione non è possibile connettersi a questo computer

Il debugger remoto può essere eseguito con un account utente diverso. Nel debugger remoto, aprire **strumenti > autorizzazioni** per aggiungere l'utente alle autorizzazioni del debugger remoto. Per ulteriori informazioni, vedere [il debugger remoto è in esecuzione con un account utente diverso](#user_accounts).

Se il messaggio di errore indica anche un firewall, il firewall nel computer locale può impedire le comunicazioni dal computer remoto, tornare a Visual Studio. Vedere [procedura](#firewall).

## <a name="access_denied"></a>Accesso negato

Questo errore viene visualizzato se si tenta di eseguire il debug in un computer remoto a 64 bit da un computer a 32 bit (non supportato).

## <a name="security_package"></a>Si è verificato un errore specifico del pacchetto di sicurezza

Può trattarsi di un problema legacy specifico di Windows XP e Windows 7. Vedere questo [informazioni](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package). 

## <a name="causes-and-recommendations"></a>Le cause e indicazioni

### <a name="dns"></a>Il computer remoto non è raggiungibile 

Se non è possibile connettersi utilizzando il nome del computer remoto, provare a usare l'indirizzo IP. È possibile utilizzare `ipconfig` in una riga di comando nel computer remoto per ottenere l'indirizzo IPv4. Se si utilizza un file host, verificare che sia configurato correttamente.

Se il problema persiste, verificare che il computer remoto sia accessibile in rete ([ping](https://technet.microsoft.com/en-us/library/cc732509(v=ws.10).aspx) il computer remoto). Non è supportato il debug remoto su Internet, tranne che in alcuni scenari di Microsoft Azure.
  
### <a name="server_incorrect"></a>Il nome del server non è corretto o software di terze parti interferisce con il debugger remoto

In Visual Studio, esaminare le proprietà del progetto e assicurarsi che il nome del server sia corretto. Vedere gli argomenti per [c# e Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) e [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Per ASP.NET, aprire **proprietà / Web / server** o **proprietà / Debug** a seconda del tipo di progetto.

> [!NOTE]
> Se si aggiungono al processo, le impostazioni di connessione remota nelle proprietà del progetto non vengono utilizzate.

Se il nome del server sia corretto, il software antivirus o un firewall di terze parti potrebbe bloccare il debugger remoto. Durante il debug in locale, questa situazione può verificarsi se Visual Studio è un'applicazione a 32 bit, pertanto utilizza la versione a 64 bit del debugger remoto per eseguire il debug di applicazioni a 64 bit. I processi a 32 e 64 bit di comunicare attraverso la rete locale nel computer locale. Il traffico di rete resta all'interno del computer, ma è possibile che un software per la sicurezza di terze parti blocchi la comunicazione.

### <a name="user_accounts"></a>Il debugger remoto è in esecuzione con un account utente diverso 

Il debugger remoto, per impostazione predefinita, accetterà solo connessioni dell'utente che ha avviato il debugger remoto e i membri del gruppo Administrators. Altri utenti devono essere concesse autorizzazioni in modo esplicito. 
 
Per risolvere il problema, usare uno dei metodi seguenti:  

-   Aggiungere l'utente di Visual Studio per le autorizzazioni del debugger remoto (nella finestra del debugger remoto, scegliere **strumenti > autorizzazioni**).

-   Nel computer remoto, riavviare il debugger remoto con lo stesso account utente e password in uso nel computer di Visual Studio.

    > [!NOTE]
    > Se si esegue il debugger remoto in un server remoto, fare doppio clic su app il Debugger remoto e scegliere **Esegui come amministratore** (oppure, è possibile eseguire il debugger remoto come servizio). Se non si vengono eseguiti in un server remoto, semplicemente avviarlo normalmente.
  
-   È possibile avviare il debugger remoto dalla riga di comando con il **/Allow \<nome utente >** parametro: `msvsmon /allow <username@computer>`. 
  
-   In alternativa, è possibile consentire agli utenti di eseguire il debug remoto. Nella finestra del debugger remoto, andare al **strumenti > Opzioni** finestra di dialogo. Se si seleziona   **Nessuna autenticazione**, è possibile selezionare **Consenti debug da parte di qualsiasi utente**. Tuttavia, è consigliabile provare questa opzione solo se le altre opzioni di esito negativo o se si utilizza una rete privata.

### <a name="firewall"></a>Il firewall nel computer remoto non consente le connessioni in ingresso al debugger remoto  
 Il firewall nel computer Visual Studio e il firewall nel computer remoto devono essere configurati per consentire la comunicazione tra Visual Studio e il debugger remoto. Per informazioni sulle porte usate dal debugger remoto, vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Per informazioni sulla configurazione del firewall di Windows, vedere [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La versione del debugger remoto non corrisponde alla versione di Visual Studio  
 La versione di Visual Studio in esecuzione in locale deve corrispondere alla versione di Remote Debugging Monitor in esecuzione nel computer remoto. Per risolvere questo problema, scaricare e installare la versione corrispondente di Remote Debugging Monitor. Per ottenere la versione corretta del debugger remoto, vedere [il debug remoto](../debugger/remote-debugging.md).
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Il computer locale e quello remoto hanno modalità di autenticazione diverse  
 Il computer locale e quello remoto devono usare la stessa modalità di autenticazione. Per risolvere questo problema, assicurarsi che entrambi i computer usino la stessa modalità di autenticazione. È possibile modificare la modalità di autenticazione. Nella finestra del debugger remoto, andare al **strumenti > Opzioni** la finestra di dialogo.
  
 Per altre informazioni sulle modalità di autenticazione, vedere [Panoramica di Autenticazione di Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>Il software antivirus sta bloccando le connessioni  
 Il software antivirus di Windows consente le connessioni del debugger remoto, mentre altri software antivirus di terze parti potrebbero bloccarle. Controllare la documentazione del software antivirus per scoprire come consentire queste connessioni.  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>I criteri di sicurezza di rete bloccano la comunicazione tra il computer remoto e Visual Studio  
 Esaminare la sicurezza della rete per assicurarsi che non blocchi la comunicazione. Per ulteriori informazioni sui criteri di sicurezza di rete di Windows, vedere [le impostazioni di criteri di sicurezza](/windows/device-security/security-policy-settings/security-policy-settings).  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>La rete è troppo occupata per supportare il debug remoto  
 Provare a eseguire il debug remoto in un altro momento oppure pianificare il lavoro sulla rete per un altro orario.  
  
## <a name="more-help"></a>Altre informazioni  
 Per ottenere assistenza sul debugger remoto più, aprire pagina della Guida del debugger remoto (**Guida > utilizzo** nel debugger remoto).
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)