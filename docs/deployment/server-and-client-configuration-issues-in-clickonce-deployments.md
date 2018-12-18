---
title: Server e i problemi di configurazione Client nelle distribuzioni ClickOnce | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b50dbe51f58af79b8c1074c592f98abccbe8ba7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce
Se si utilizza Internet Information Services (IIS) in Windows Server e la distribuzione contiene un tipo di file che non viene riconosciuta, ad esempio un file di Microsoft Word, IIS rifiuta la trasmissione del file e la distribuzione avrà esito negativo.  
  
 Inoltre, alcuni server Web e Web, applicazioni, ad esempio [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contiene un elenco di file e tipi di file che non è possibile scaricare. Ad esempio, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] impedisce il download di tutti i file Web. config. Questi file possono contenere informazioni riservate, ad esempio nomi utente e password.  
  
 Nonostante questa limitazione non dovrebbe causare problemi per il download dei componenti di base [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file, ad esempio i manifesti e assembly, questa restrizione può impedire il download di file di dati inclusi come parte del [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. In [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è possibile risolvere l'errore rimuovendo il gestore che impedisce il download di questi file da Gestione configurazione di IIS. Vedere la documentazione del server IIS per altri dettagli.  
  
 Alcuni server Web potrebbero bloccare i file con estensione dll,. config e mdf. Applicazioni basate su Windows in genere includono i file con alcune di queste estensioni. Se un utente tenta di eseguire un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che accede a un file bloccato in un server Web, verrà generato un errore. Anziché lo sblocco di tutte le estensioni di file, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ogni file di applicazione con un'estensione di file "deploy" viene pubblicato per impostazione predefinita. Pertanto, l'amministratore deve solo configurare il server Web per sbloccare le estensioni di tre file seguenti:  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 Tuttavia, è possibile disabilitare questa opzione deselezionando la **Usa estensione ". deploy"** opzione il [pubblicare la finestra di dialogo Opzioni](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), nel qual caso è necessario configurare il server Web per sbloccare tutte le estensioni di file utilizzata dall'applicazione.  
  
 È necessario configurare manifest, Application e deploy, ad esempio, se si utilizza IIS in cui non è installato il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o se si utilizza un altro server Web (ad esempio Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) e ClickOnce  
 Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione funziona correttamente su SSL, tranne in Internet Explorer genera una richiesta sul certificato SSL. Il prompt dei comandi può essere generato quando si verifica un problema con il certificato, ad esempio quando i nomi dei siti non corrispondono o il certificato è scaduto. Per rendere [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lavoro in una connessione SSL, verificare che il certificato sia aggiornato e che i dati del certificato corrispondano ai dati del sito.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce e l'autenticazione del Proxy  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]fornisce supporto per l'autenticazione integrata di Windows del proxy a partire da .NET Framework 3.5. Nessun direttive Machine. config specifico sono necessari. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]non fornisce supporto per altri protocolli di autenticazione, ad esempio di base o Digest.  
  
 È inoltre possibile applicare un hotfix per .NET Framework 2.0 per abilitare questa funzionalità. Per ulteriori informazioni, vedere http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Per ulteriori informazioni, vedere [ \<defaultProxy > Element (Network Settings)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce e compatibilità di Web Browser  
 Attualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installazioni verranno avviato solo se l'URL del manifesto di distribuzione viene aperto con Internet Explorer. Una distribuzione il cui URL avviato da un'altra applicazione, ad esempio Microsoft Office Outlook, verrà avviata correttamente solo se è impostato Internet Explorer come browser predefinito.  
  
> [!NOTE]
>  Mozilla Firefox è supportato se il provider di distribuzione non è vuoto o è installata l'estensione di Microsoft .NET Framework Assistant. Questa estensione è inclusa in .NET Framework 3.5 SP1. Per il supporto XBAP, il plug-in NPWPF viene attivata quando necessario.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Attivazione delle applicazioni ClickOnce tramite Scripting di Browser  
 Se si hanno sviluppato una pagina Web personalizzata che consente di avviare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione mediante l'esecuzione di script attivo, è possibile che l'applicazione non verrà avviata in alcuni computer. Internet Explorer contiene un'impostazione denominata **richiesta automatica per il download dei file**, che influisce su questo comportamento. Questa impostazione è disponibile nel **sicurezza** nella scheda relativa **opzioni** menu che influisce su questo comportamento. Viene chiamato **richiesta automatica per il download dei file**, ed è elencata sotto il **Scarica** categoria. La proprietà è impostata su **abilitare** per impostazione predefinita per le pagine Web intranet e **disabilitare** per impostazione predefinita per le pagine Web di Internet. Quando questa impostazione è impostata su **disabilitare**, qualsiasi tentativo di attivare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione a livello di codice (ad esempio, assegnando il relativo URL per il `document.location` proprietà) verrà bloccato. In questo caso, gli utenti possono avviare le applicazioni solo tramite un download avviato dall'utente, ad esempio, facendo clic su un collegamento ipertestuale impostato l'URL dell'applicazione.  
  
## <a name="additional-server-configuration-issues"></a>Problemi di configurazione aggiuntive del Server  
  
##### <a name="administrator-permissions-required"></a>Autorizzazioni di amministratore necessarie  
 Se esegue la pubblicazione tramite HTTP, è necessario disporre delle autorizzazioni di amministratore nel server di destinazione. IIS richiede questo livello di autorizzazioni. Se non si esegue la pubblicazione tramite HTTP, è solo necessario autorizzazione di scrittura sul percorso di destinazione.  
  
##### <a name="server-authentication-issues"></a>Problemi di autenticazione server  
 Durante la pubblicazione in un server remoto con "L'accesso anonimo" disattivata, verrà visualizzato l'avviso seguente:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  È possibile configurare l'autenticazione NTLM (NT richiesta-risposta) modo se il sito richiede credenziali diverse dalle credenziali predefinite e, nella finestra di dialogo sicurezza, si fa clic su **OK** quando viene chiesto se si desidera salvare fornito credenziali per le sessioni future. Tuttavia, questa soluzione non funzionerà per l'autenticazione di base.  
  
## <a name="using-third-party-web-servers"></a>Utilizzo di server Web di terze parti  
 Se si distribuisce un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione da un server Web diversi da IIS, che si verifichi un problema se il server restituisce il tipo di contenuto non corretto per la chiave [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file, ad esempio il manifesto di distribuzione e manifesto dell'applicazione. Per risolvere questo problema, vedere la Guida del server Web documentazione su come aggiungere nuovi tipi di contenuto al server e assicurarsi che tutti i mapping estensione nome di file elencati nella tabella seguente sono presenti.  
  
|Estensione di file|Tipo di contenuto|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>Le unità mappate e ClickOnce  
 Se si utilizza Visual Studio per pubblicare un'applicazione ClickOnce, è possibile specificare un'unità mappata come percorso di installazione. Tuttavia, è possibile modificare l'applicazione ClickOnce per installare da un'unità mappata tramite l'Editor (Mage.exe e MageUI.exe) e il generatore di manifesti. Per ulteriori informazioni, vedere [Mage.exe (generazione manifesto e lo strumento di modifica)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) e [MageUI.exe (strumento di modifica, Client grafico e la generazione del manifesto)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Il protocollo FTP non è supportato per l'installazione di applicazioni  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]supporta l'installazione di applicazioni da qualsiasi file server o un server Web HTTP 1.1. FTP, il protocollo di trasferimento di File, non è supportato per l'installazione di applicazioni. È possibile utilizzare FTP per pubblicare solo le applicazioni. Nella tabella seguente vengono riepilogate le differenze:  
  
|Tipo di URL|Descrizione|  
|--------------|-----------------|  
|FTP: / /|È possibile pubblicare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
|http://|È possibile installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
|https://|È possibile installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
|file://|È possibile installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall  
 Per impostazione predefinita, Windows XP SP2 è abilitato Windows Firewall. Se si sviluppa l'applicazione in un computer con sistema operativo Windows XP, si è ancora in grado di pubblicare ed eseguire [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni dal server locale che esegue IIS. Tuttavia, è possibile accedere il server che esegue IIS da un altro computer, a meno che non si apre il Firewall di Windows. Per istruzioni sulla gestione di Windows Firewall, vedere la Guida di Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Abilita le estensioni del server di FrontPage  
 Estensioni del Server di FrontPage di Microsoft è obbligatorio per la pubblicazione di applicazioni in un server Web di Windows che utilizza il protocollo HTTP.  
  
 Per impostazione predefinita, Windows Server non dispone di estensioni del Server di FrontPage installate. Se si desidera utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per pubblicare in un server Web di Windows Server che utilizza HTTP con estensioni del Server, è necessario installare prima le estensioni del Server di FrontPage. È possibile eseguire l'installazione utilizzando lo strumento di amministrazione di gestione Server in Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Tipi di contenuto bloccato  
 IIS in [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] bloccati tutti i tipi di file ad eccezione di alcuni tipi di contenuto noti (ad esempio, con estensione htm, HTML,. txt e così via). Per abilitare la distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni che utilizzano questo server, è necessario modificare le impostazioni di IIS per consentire il download dei file di estensione Application manifest e altri tipi di file personalizzati utilizzati dall'applicazione.  
  
 Se si distribuisce tramite un server IIS, eseguire inetmgr.exe e aggiungere nuovi tipi di File per la pagina Web predefinita:  
  
-   Per le estensioni Application e manifest, il tipo MIME deve essere "application/x-ms-application". Per altri tipi di file, il tipo MIME deve essere "application/octet-stream".  
  
-   Se si crea un tipo MIME con l'estensione "*" e il tipo MIME "application/octet-stream", sarà possibile sbloccare i file di tipo per essere scaricato. (Tuttavia bloccate file non è possibile scaricare i tipi, ad esempio con estensione aspx e. asmx).  
  
 Per istruzioni dettagliate sulla configurazione dei tipi MIME in Windows Server, fare riferimento all'articolo della Microsoft Knowledge Base KB326965, "IIS 6.0 non non servire MIME tipi sconosciuti" in [http://support.microsoft.com/default.aspx?scid=kb;en-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mapping dei tipi di contenuto  
 Quando si pubblica su HTTP, il tipo di contenuto (noto anche come tipo MIME) per il file con estensione Application deve essere "application/x-ms-application". Se dispone di [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] installato nel server, questo verrà impostato automaticamente. Se questo non è installato, quindi è necessario creare un'associazione di tipo MIME per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] radice virtuale dell'applicazione (o l'intero server).  
  
 Se si distribuisce tramite un server IIS, eseguire inetmgr.exe e aggiungere un nuovo tipo di contenuto di "application/x-ms-application" per l'estensione Application.  
  
## <a name="http-compression-issues"></a>Problemi relativi alla compressione HTTP  
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è possibile eseguire i download che utilizzano la compressione HTTP, una tecnologia di server Web che utilizza l'algoritmo GZIP per comprimere un flusso di dati prima di inviarli al client. Il client, in questo caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]: decomprime il flusso prima di leggere i file.  
  
 Se si utilizza IIS, è possibile abilitare facilmente la compressione HTTP. Tuttavia, quando si abilita la compressione HTTP, disponibile solo per determinati tipi di file, vale a dire, HTML e file di testo. Per abilitare la compressione per gli assembly (DLL), XML (XML), i manifesti di distribuzione (Application) e i manifesti dell'applicazione (con estensione manifest), è necessario aggiungere questi tipi di file all'elenco di tipi per IIS da comprimere. Finché non verranno aggiunti i tipi di file per la distribuzione, vengono compresse solo file di testo e HTML.  
  
 Per istruzioni dettagliate per IIS, vedere [come specificare i tipi di documenti aggiuntive per la compressione HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi delle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)