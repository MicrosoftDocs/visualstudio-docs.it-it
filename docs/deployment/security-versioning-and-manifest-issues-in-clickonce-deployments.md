---
title: Sicurezza e controllo delle versioni manifesti problemi nelle distribuzioni ClickOnce | Documenti Microsoft
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
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 53f9c0114573c6f08a2d9219e4dd2028ffe9ac7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemi relativi alla sicurezza, al controllo delle versioni e ai manifesti nelle distribuzioni ClickOnce
Esistono una serie di problemi con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] protezione, controllo delle versioni dell'applicazione e manifesto sintassi e semantica che può causare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione non corretta.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>Controllo Account utente di Windows Vista e ClickOnce  
 In [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], esecuzione di applicazioni per impostazione predefinita come utente standard, anche se l'utente corrente è connesso con un account che disponga delle autorizzazioni di amministratore. Se un'applicazione deve eseguire un'azione che richiede le autorizzazioni di amministratore, indica al sistema operativo, che quindi chiede all'utente di immettere le credenziali di amministratore. Questa funzionalità, denominata controllo Account utente (UAC), impedisce alle applicazioni di apportare modifiche che possono interessare l'intero sistema operativo senza l'approvazione esplicita di un utente. Le applicazioni Windows dichiarano che richiedono l'elevazione delle autorizzazioni, specificando il `requestedExecutionLevel` attributo la `trustInfo` sezione del manifesto dell'applicazione.  
  
 A causa del rischio di esporre le applicazioni ad attacchi di elevazione dei privilegi di sicurezza, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se questa opzione è abilitata per il client, le applicazioni non è possibile richiedere l'elevazione delle autorizzazioni. Qualsiasi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che tenta di impostare il relativo `requestedExecutionLevel` attributo `requireAdministrator` o `highestAvailable` non verranno installati nei [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 In alcuni casi, il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione potrebbe tentare di eseguire con autorizzazioni di amministratore a causa di logica di rilevamento del programma di installazione in [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. In questo caso, è possibile impostare il `requestedExecutionLevel` attributo nel manifesto dell'applicazione per `asInvoker`. In questo modo l'applicazione per l'esecuzione senza l'elevazione dei privilegi. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]Questo attributo viene aggiunto automaticamente a tutti i manifesti dell'applicazione.  
  
 Se si sviluppa un'applicazione che richiede le autorizzazioni di amministratore per l'intera durata dell'applicazione, è consigliabile distribuire l'applicazione utilizzando invece la tecnologia Windows Installer (MSI). Per ulteriori informazioni, vedere [nozioni fondamentali di Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Applicazioni con attendibilità parziale e quote per le applicazioni online  
 Se il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è in esecuzione in modalità online anziché un'installazione, è necessario che la quota impostata per le applicazioni in linea. Inoltre, un'applicazione di rete che viene eseguito in attendibilità parziale, ad esempio con un set limitato di autorizzazioni di sicurezza, non può essere superiore alla metà della quota.  
  
 Per ulteriori informazioni e istruzioni su come modificare la quota di applicazione in linea, vedere [Cenni preliminari sulla Cache di ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problemi di controllo delle versioni  
 Potrebbero verificarsi problemi se si assegnano nomi sicuri per l'assembly e incrementare il numero di versione di assembly in modo da riflettere l'aggiornamento di un'applicazione. Qualsiasi assembly compilato con un riferimento a un assembly con nome sicuro deve essere ricompilato o tenta di fare riferimento alla versione precedente dell'assembly. L'assembly verrà provare questa perché l'assembly è utilizzato il valore della versione precedente nella richiesta di associazione.  
  
 Ad esempio, si dispone di un assembly con nome sicuro nel proprio progetto con versione 1.0.0.0. Dopo aver compilato l'assembly, aggiungerlo come riferimento al progetto che contiene l'applicazione principale. Se si aggiorna l'assembly, incrementa la versione 1.0.0.1 e provare a eseguire la distribuzione senza ricompilare l'applicazione, l'applicazione non sarà in grado di caricare l'assembly in fase di esecuzione.  
  
 Questo errore può verificarsi solo se si sta modificando il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti manualmente; non dovrebbero verificarsi questo errore se si genera la distribuzione tramite [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Specificare i singoli assembly .NET Framework nel manifesto  
 L'applicazione non verrà caricato se è stata modificata manualmente un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione per fare riferimento a una versione precedente di un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assembly. Ad esempio, se è stato aggiunto un riferimento all'assembly System.Net per una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] prima della versione specificata nel manifesto, quindi verrebbe generato un errore. In generale, non tentare di specificare riferimenti a singoli [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assembly, come la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in cui viene eseguita l'applicazione è specificato come una dipendenza nel manifesto dell'applicazione.  
  
## <a name="manifest-parsing-issues"></a>Analisi dei problemi di manifesti  
 I file manifesto utilizzati da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono file XML e devono essere sia ben formato e valido: devono rispettare le regole di sintassi XML e utilizzare solo gli elementi e attributi definiti nello schema XML pertinente.  
  
 Un elemento che può causare problemi in un file manifesto consiste nel selezionare un nome per l'applicazione che contiene un carattere speciale, ad esempio un segno di virgolette singolo o doppio. Nome dell'applicazione fa parte del relativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identità. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]attualmente non analizza le identità che contengono caratteri speciali. Se l'applicazione attivazione ha esito negativo, verificare che usano solo lettere e cifre per il nome e tentare di distribuirla nuovamente.  
  
 Se è stata modificata manualmente i manifesti di distribuzione o dell'applicazione, si potrebbe essere involontariamente danneggiato li. Impedendo così una corretta [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installazione. È possibile eseguire il debug di tali errori in fase di esecuzione facendo clic su **dettagli** sul **errore ClickOnce** la finestra di dialogo, la lettura del messaggio di errore nel log. Nel log verrà visualizzato uno dei due messaggi seguenti:  
  
-   Una descrizione dell'errore di sintassi e il numero di riga e carattere posizione in cui si è verificato l'errore.  
  
-   Il nome di un elemento o attributo utilizzato in violazione dello schema del manifesto. Se sono stati aggiunti manualmente XML per i manifesti, è necessario confrontare le aggiunte agli schemi del manifesto. Per ulteriori informazioni, vedere [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) e [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
-   Un conflitto di ID. Riferimenti a dipendenze nei manifesti di distribuzione e dell'applicazione devono essere univoci in entrambi i `name` e `publicKeyToken` gli attributi. Se entrambi gli attributi corrispondono tra qualsiasi due elementi all'interno di un manifesto, l'analisi del manifesto non avrà esito positivo.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauzioni relative alla modifica manuale dei manifesti o applicazioni  
 Quando si aggiorna un manifesto dell'applicazione, è necessario firmare nuovamente sia il manifesto dell'applicazione e il manifesto di distribuzione. Il manifesto di distribuzione contiene un riferimento al manifesto dell'applicazione che include l'hash del file e la firma digitale.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Precauzioni relative all'utilizzo di utilizzo del Provider di distribuzione  
 Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto della distribuzione è un `deploymentProvider` proprietà che fa riferimento al percorso completo della posizione da in cui l'applicazione deve essere installato e servita:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Questo percorso viene impostato quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea l'applicazione ed è obbligatorio per le applicazioni installate. Il percorso punta alla posizione standard in cui il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programma di installazione installerà l'applicazione da e ricerca di aggiornamenti. Se si utilizza il **xcopy** comando per copiare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in un percorso diverso, ma non si modifica il `deploymentProvider` proprietà [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] faranno ancora riferimento nuovamente nel percorso originale durante il tentativo di scaricare il applicazione.  
  
 Se si desidera spostare o copiare un'applicazione, è necessario aggiornare anche il `deploymentProvider` percorso, in modo che il client esegua effettivamente l'installazione dalla nuova posizione. L'aggiornamento del percorso è principalmente un problema se sono installate le applicazioni. Per le applicazioni online che sono sempre avviate tramite l'URL originale, l'impostazione di `deploymentProvider` è facoltativo. Se `deploymentProvider` è impostata, ne verrà utilizzato il valore; in caso contrario, verrà utilizzato l'URL utilizzato per avviare l'applicazione come URL di base per scaricare i file dell'applicazione.  
  
> [!NOTE]
>  Ogni volta che si aggiorna il manifesto è necessario anche firmarlo nuovamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi delle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)