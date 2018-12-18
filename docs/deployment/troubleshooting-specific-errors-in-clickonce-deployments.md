---
title: Risoluzione dei problemi relativi a errori specifici nelle distribuzioni ClickOnce | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: ffa7449347fe5e898f2984237dfc8908e3bb2003
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Risoluzione di errori specifici nelle distribuzioni ClickOnce
Questo argomento vengono elencati gli errori comuni che possono verificarsi quando si distribuisce un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , applicazione e fornisce i passaggi per risolvere i problemi.  
  
## <a name="general-errors"></a>Errori generali  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Quando si tenta di individuare un file con estensione Application, non accade nulla o esegue il rendering XML in Internet Explorer o si riceve una finestra di dialogo Esegui o Salva con nome  
 Questo errore è probabilmente dovuto a tipi di contenuto (noto anche come tipi MIME) registrati non corretta nel server o nel client.  
  
 Innanzitutto, assicurarsi che il server è configurato per associare l'estensione Application con tipo di contenuto "application/x-ms-application".  
  
 Se il server è configurato correttamente, verificare che il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] è installato nel computer in uso. Se il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] è installato, viene ancora visualizzato questo problema, provare a disinstallare e reinstallare il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] per registrare nuovamente il tipo di contenuto nel client.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Errore viene visualizzato il messaggio "Impossibile recuperare l'applicazione. I file mancanti nella distribuzione"o"download dell'applicazione è stata interrotta, verificare la presenza di errori di rete e riprovare più tardi"  
 Questo messaggio indica che uno o più file a cui fa riferimento il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti non possono essere scaricati. Il modo più semplice per risolvere l'errore è tentare di scaricare l'URL che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è possibile eseguire il download. Ecco alcune possibili cause:  
  
-   Se il file di log è indicato "(403) accesso negato" o "(404) non trovata", verificare che il server Web sia configurato in modo che non blocca il download del file. Per altre informazioni, vedere [Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Se il file. config viene bloccato dal server, vedere la sezione "errore di Download quando si tenta di installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che dispone di un file con estensione config" più avanti in questo argomento.  
  
-   Determinare se si è verificato il `deploymentProvider` URL nel manifesto di distribuzione punta a una posizione diversa dall'URL utilizzato per l'attivazione.  
  
-   Assicurarsi che tutti i file siano presenti sul server. il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] log dovrebbero essere il file di cui non è stato trovato.  
  
-   Verificare se sono presenti problemi di connettività di rete; è possibile ricevere questo messaggio se il computer client era offline durante il download.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Errore durante il download, quando si tenta di installare un'applicazione ClickOnce che dispone di un file con estensione config  
 Per impostazione predefinita, un'applicazione basata su Windows di Visual Basic include un file app. config. Esisterà un problema quando un utente tenta di installare un server Web che utilizza Windows Server 2003, poiché tale sistema operativo blocca l'installazione del file config per motivi di sicurezza. Per abilitare il file config sia installato, fare clic su **Usa estensione ". deploy"** nel **opzioni di pubblicazione** la finestra di dialogo.  
  
 È inoltre necessario impostare i tipi di contenuto (noto anche come tipi MIME) in modo appropriato per Application manifest e il file. deploy. Per ulteriori informazioni, vedere la documentazione del server.  
  
 Per ulteriori informazioni, vedere "Windows Server 2003: tipi di contenuto bloccati" in [Server e i problemi di configurazione Client nelle distribuzioni ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Messaggio di errore: "Applicazione non è formattata correttamente;" File di log contiene "firma XML è valido"  
 Assicurarsi di aggiornare il file manifesto e nuovamente firmato. Ripubblicare l'applicazione utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oppure utilizzare Mage per firmare nuovamente l'applicazione.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>È stato aggiornato l'applicazione nel server, ma il client non scarica l'aggiornamento  
 Questo problema potrebbe essere risolto eseguendo una delle seguenti operazioni:  
  
-   Esaminare il `deploymentProvider` URL nel manifesto di distribuzione. Verificare che si siano aggiornando i bit nello stesso percorso che `deploymentProvider` punta a.  
  
-   Verificare l'intervallo di aggiornamento nel manifesto di distribuzione. Se questo intervallo è impostato su intervalli periodici, ad esempio una volta ogni sei ore [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non analizzeranno per un aggiornamento prima che sia trascorso questo intervallo. È possibile modificare il manifesto per l'analisi per un aggiornamento ogni volta che viene avviata l'applicazione. Modifica dell'intervallo di aggiornamento è un'opzione utile durante la fase di sviluppo per verificare gli aggiornamenti vengono installati, ma rallenta l'attivazione dell'applicazione.  
  
-   Provare a riavviare l'applicazione nel menu Start. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]sia stato rilevato l'aggiornamento in background, ma verrà richiesto di installare i componenti aggiornati alla successiva attivazione.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante l'aggiornamento verrà visualizzato un errore con la seguente voce di log: "il riferimento nella distribuzione non corrisponde all'identità definita nel manifesto dell'applicazione"  
 Questo errore può verificarsi perché è stata modificata manualmente i manifesti di distribuzione e dell'applicazione e hanno causato la descrizione dell'identità di un assembly in un manifesto da risultare non sincronizzati con le altre. L'identità di un assembly è costituito da nome, versione, impostazioni cultura e token di chiave pubblica. Esaminare le descrizioni di identità nei manifesti e correggere eventuali differenze.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Prima attivazione da CD-ROM o un disco locale viene eseguita correttamente, mentre quella successiva dal Menu Start non riesce.  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]utilizza l'URL di Provider di distribuzione per ricevere gli aggiornamenti dell'applicazione. Verificare che il percorso che fa riferimento l'URL sia corretto.  
  
#### <a name="error-cannot-start-the-application"></a>Errore: "Impossibile avviare l'applicazione"  
 Questo messaggio di errore indica in genere che si verifica un problema di installazione dell'applicazione nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archiviare. L'applicazione contiene un errore o l'archivio è danneggiato. Il file di log potrebbe indicare la posizione dell'errore.  
  
 È necessario eseguire le operazioni seguenti:  
  
-   Verificare che l'identità del manifesto di distribuzione, il manifesto dell'applicazione e identità dell'applicazione principale EXE siano tutti univoci.  
  
-   Verificare che i percorsi dei file non siano più di 100 caratteri. Se l'applicazione contiene percorsi di file che sono troppo lunghi, è possibile superare le limitazioni relative al percorso massimo che è possibile archiviare. Provare ad abbreviare i percorsi e reinstallare.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Impostazioni di PrivatePath nel file config dell'applicazione non vengono rispettate.  
 Per utilizzare l'attributo PrivatePath (percorsi di sondaggio Fusion), l'applicazione deve richiedere autorizzazioni di attendibilità. Provare a modificare il manifesto dell'applicazione per richiedere l'attendibilità totale e riprovare.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante la disinstallazione verrà visualizzato un messaggio per segnalare che "Non è stato possibile disinstallare l'applicazione"  
 Questo messaggio indica in genere che l'applicazione è già stato rimosso o l'archivio è danneggiato. Dopo aver fatto clic **OK**, **il programma di installazione** voce viene rimossa.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante l'installazione, viene visualizzato un messaggio indicante che le dipendenze della piattaforma non sono installate.  
 Manca un prerequisito nella GAC (cache di assembly globale) necessarie per eseguire l'applicazione.  
  
## <a name="publishing-with-visual-studio"></a>Pubblicazione con Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>La pubblicazione in Visual Studio non riesce  
 Assicurarsi di aver il diritto di pubblicare il server di destinazione. Ad esempio, se si è connessi a un computer di terminal server come utente normale, non come amministratore, probabilmente non è i diritti necessari per pubblicare nel server Web locale.  
  
 Se esegue la pubblicazione con un URL, assicurarsi che il computer di destinazione dispone di estensioni del Server abilitata.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Messaggio di errore: Impossibile creare il sito Web '\<sito >'. Non sono installati i componenti per la comunicazione con le estensioni del Server di FrontPage.  
 Verificare di disporre di Microsoft Visual Studio Web Authoring installato il componente nel computer in cui esegue la pubblicazione. Per gli utenti di Express, questo componente non è installato per impostazione predefinita. Per ulteriori informazioni, vedere [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Messaggio di errore: Impossibile trovare il file ' Microsoft.Windows.Common-controlli, Version = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, tipo = win32'  
 Questo messaggio di errore viene visualizzato quando si tenta di pubblicare un'applicazione WPF con gli stili visuali abilitati. Per risolvere questo problema, vedere [procedura: pubblicare un'applicazione WPF con abilitato stili Visual](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Utilizzo di Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Si è tentato di accedere con un certificato nell'archivio dei certificati e una casella ricevuto alcun messaggio  
 Nel **firma** la finestra di dialogo, è necessario:  
  
-   Selezionare **accesso con un certificato archiviato**, e  
  
-   Selezionare un certificato dall'elenco. il primo certificato non è selezionata l'impostazione predefinita.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Fare clic sul pulsante "Accedi" non"genera un'eccezione  
 Questo problema è un bug noto. Tutti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti sono devono essere firmati. Selezionare una delle opzioni di firma e quindi fare clic su **OK**.  
  
## <a name="additional-errors"></a>Altri errori  
 La tabella seguente illustra alcuni comuni messaggi di errore che un computer client possono essere visualizzati quando l'utente installa un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Ogni messaggio di errore è elencato accanto a una descrizione della causa più probabile dell'errore.  
  
|Messaggio di errore|Descrizione|  
|-------------------|-----------------|  
|Impossibile avviare l'applicazione. Contattare l'autore dell'applicazione.<br /><br /> Impossibile avviare l'applicazione. Per assistenza, contattare il fornitore dell'applicazione.|Si tratta di messaggi di errore generico che si verificano quando l'applicazione non può essere avviato, ed non è disponibile nessun altro motivo specifico. Spesso questo significa che l'applicazione è danneggiata o che il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivio è danneggiato.|  
|Impossibile continuare. Non è formattato correttamente l'applicazione. Per assistenza, contattare l'autore dell'applicazione.<br /><br /> Convalida dell'applicazione non riuscita. Impossibile continuare.<br /><br /> Impossibile recuperare i file dell'applicazione. I file danneggiano nella distribuzione.|Uno dei file manifesti della distribuzione è sintatticamente non valido o contiene un hash che non può essere riconciliato con il file corrispondente. Questo errore può inoltre indicare che il manifesto incorporato all'interno di un assembly è danneggiato. Creare una nuova distribuzione e ricompilare l'applicazione, o trovare e correggere gli errori manualmente nei manifesti.|  
|Impossibile recuperare l'applicazione. Errore di autenticazione.<br /><br /> Installazione dell'applicazione non riuscita. Impossibile trovare il file di applicazioni nel server. Per assistenza, contattare l'autore dell'applicazione o l'amministratore.|Impossibile scaricare uno o più file nella distribuzione perché non si dispone dell'autorizzazione per accedervi. Questo può dipendere da un errore 403 accesso negato, restituito da un server Web, che può verificarsi se uno dei file nella distribuzione termina con un'estensione che rende il server Web di considerarlo come un file protetto. Inoltre, una directory che contiene uno o più i file dell'applicazione potrebbe richiedere un nome utente e una password per accedere.|  
|Non è possibile scaricare l'applicazione. Mancano alcuni file necessari. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema.|Impossibile trovare uno o più file elencati nel manifesto dell'applicazione nel server. Verificare di avere caricato i file dipendenti di distribuzione, quindi riprovare.|  
|Download dell'applicazione non riuscita. Controllare la connessione di rete o contattare l'amministratore di sistema o di un provider di servizi di rete.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Impossibile stabilire una connessione di rete al server. Esaminare la disponibilità del server e lo stato della rete.|  
|URLDownloadToCacheFile non riuscita con HRESULT '\<numero >'. Si è verificato un errore durante il tentativo di scaricare '\<file >'.|Se un utente ha impostato opzione sicurezza avanzata di Internet Explorer "Avvisa se si passa tra sicuro e modalità non protetta" nel computer di destinazione di distribuzione e l'URL di installazione dell'applicazione ClickOnce in corso l'installazione viene reindirizzata da non protetta a un sito sicuro (o viceversa), l'installazione avrà esito negativo perché l'avviso di Internet Explorer interrotta.<br /><br /> Per risolvere questo problema, è possibile eseguire una delle operazioni seguenti:<br /><br /> -Deselezionare l'opzione di sicurezza.<br />-Verificare assicurarsi che l'URL di installazione non viene reindirizzata in modo tale che cambia modalità di sicurezza.<br />-Rimuovere completamente il reindirizzamento e scegliere l'URL di installazione effettivo.|  
|Si è verificato un errore di scrittura sul disco rigido. Potrebbero non essere disponibile spazio sufficiente sul disco. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema.|Potrebbe trattarsi di spazio su disco insufficiente per l'applicazione, ma può anche indicare un errore dei / o più generale quando si sta tentando di salvare i file dell'applicazione per l'unità.|  
|Impossibile avviare l'applicazione. Non c'è spazio insufficiente sul disco.|Il disco è pieno. Rendere disponibile dello spazio e provare a eseguire nuovamente l'applicazione.|  
|Tentativo di caricare contemporaneamente troppe attivazioni distribuite.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Limita il numero di applicazioni che è possibile avviare contemporaneamente. Si tratta principalmente per proteggere da tentativi di attacchi di tipo denial of service contro locale provocare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] servizio; gli utenti che tenta di avviare più volte, la stessa applicazione in rapida successione, potrà solo con una singola istanza di applicazione.|  
|Tasti di scelta rapida non può essere attivate attraverso la rete.|Tasti di scelta rapida per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione può essere avviata solo sul disco rigido locale. E non tramite un URL che punta a un file di scelta rapida in un server remoto.|  
|L'applicazione è troppo grande per essere eseguita in linea in attendibilità parziale. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema.|Un'applicazione in esecuzione in attendibilità parziale non può essere superiore alla metà della dimensione della quota di applicazione in linea, che per impostazione predefinita è 250 MB.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)