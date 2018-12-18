---
title: Protezione di applicazioni ClickOnce | Documenti Microsoft
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
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: "32"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 1923c39669d50303f907974816fbb54297c477c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-security-and-deployment"></a>Sicurezza e distribuzione di ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]è una tecnologia di distribuzione che consente di creare applicazioni basate su Windows aggiornamento automatico che possono essere installate ed eseguite l'intervento dell'utente minima. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]fornisce supporto completo per la pubblicazione e aggiornamento di applicazioni distribuite con la tecnologia ClickOnce se è stata sviluppata i progetti con Visual Basic e Visual c#. Per informazioni sulla distribuzione di applicazioni Visual C++, vedere [distribuzione ClickOnce per applicazioni Visual C++](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]è possibile superare tre problemi principali della distribuzione:  
  
-   **Difficoltà nell'aggiornamento delle applicazioni.** Con la distribuzione di Microsoft Windows Installer, ogni volta che viene aggiornata un'applicazione, l'utente può installare un aggiornamento, un file msp e applicarlo al prodotto installato. con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione, è possibile fornire gli aggiornamenti automaticamente. Vengono scaricate solo le parti dell'applicazione che sono stati modificati, e reinstallata l'applicazione completa e aggiornata da una nuova cartella side-by-side.  
  
-   **Impatto sul computer dell'utente.** Con la distribuzione di Windows Installer, le applicazioni spesso si basano su componenti condivisi, con la possibilità di conflitti di versioni. con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione, ogni applicazione è indipendente e non può interferire con altre applicazioni.  
  
-   **Autorizzazioni di sicurezza.** Distribuzione di Windows Installer richiede autorizzazioni amministrative e consente solo per l'installazione utente limitati. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione consente agli utenti senza privilegi di amministratore installare, concedendo solo le autorizzazioni di sicurezza dall'accesso di codice necessarie per l'applicazione.  
  
 In passato, questi problemi causati talvolta gli sviluppatori di creare applicazioni Web anziché applicazioni basate su Windows, compromettere un'interfaccia utente avanzata per agevolare l'installazione. Tramite le applicazioni distribuite con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è possibile ottenere il meglio di entrambe le tecnologie.  
  
## <a name="what-is-a-clickonce-application"></a>Che cos'è un'applicazione ClickOnce?  
 Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è qualsiasi Windows Presentation Foundation (XBAP), Windows Form (.exe), l'applicazione console (.exe) o soluzione Office (con estensione dll) pubblicata mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia. È possibile pubblicare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in tre modi diversi: da una pagina Web, da una condivisione di file di rete o da supporto, ad esempio un CD-ROM. Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione può essere installata nel computer dell'utente finale ed eseguita localmente anche quando il computer è offline, oppure può essere eseguita in modalità solo online senza alcuna operazione di installazione in modo permanente nel computer dell'utente finale. Per altre informazioni, vedere [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni possono essere di aggiornamento automatico; è possibile cercare le versioni più recenti non appena diventano disponibili e sostituire automaticamente i file aggiornati. Lo sviluppatore può specificare il comportamento di aggiornamento. un amministratore di rete può inoltre controllare le strategie di aggiornamento, ad esempio, contrassegnare un aggiornamento come obbligatorio. Gli aggiornamenti possono anche possibile eseguire il rollback a una versione precedente dall'utente finale o da un amministratore. Per ulteriori informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Poiché [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni risultano isolate, installare o eseguire un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione non è possibile interrompere le applicazioni esistenti. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni sono indipendenti. ogni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è installata ed eseguita da una cache sicura specifica-utente, per ogni applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni eseguite nelle aree di protezione Internet o Intranet. Se necessario, l'applicazione può richiedere le autorizzazioni di sicurezza con privilegi elevati. Per altre informazioni, vedere [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Come funziona la sicurezza ClickOnce  
 Il core [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] protezione si basa sui certificati, i criteri di sicurezza di accesso di codice e la richiesta di attendibilità di ClickOnce.  
  
### <a name="certificates"></a>Certificati  
 Per verificare l'autenticità dell'editore dell'applicazione vengono utilizzati i certificati Authenticode. Utilizzando la tecnologia Authenticode per la distribuzione di applicazioni ClickOnce consente di impedire che un programma dannoso basato sulla creazione di se stesso come programma legittimo provenienti da un'origine definita e attendibile. Facoltativamente, i certificati possono essere utilizzati anche per firmare l'applicazione e i manifesti di distribuzione per dimostrare che i file non sono stati alterati. Per ulteriori informazioni, vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Certificati possono essere usati anche per configurare i computer client per un elenco di editori attendibili. Se un'applicazione proviene da un autore attendibile, può essere installato senza alcuna interazione dell'utente. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Sicurezza per l'accesso al codice  
 Sicurezza dall'accesso di codice consente di limitare l'accesso alle risorse protette del codice. Nella maggior parte dei casi, è possibile scegliere le aree Internet o Intranet locale per limitare le autorizzazioni. Utilizzare il **sicurezza** nella pagina di **ProjectDesigner** per richiedere l'area appropriata per l'applicazione. È anche possibile eseguire il debug di applicazioni con autorizzazioni limitate per emulare l'esperienza dell'utente finale. Per altre informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Richiesta di attendibilità ClickOnce  
 Se l'applicazione richiede più autorizzazioni consente la zona, l'utente finale può essere richiesto di prendere una decisione di attendibilità. L'utente finale può decidere se le applicazioni ClickOnce, ad esempio le applicazioni Windows Form, applicazioni Windows Presentation Foundation, applicazioni console, applicazioni browser XAML e le soluzioni Office sono attendibili per l'esecuzione. Per ulteriori informazioni, vedere [procedura: configurare il comportamento dei messaggi di richiesta attendibilità di ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Funzionamento della distribuzione ClickOnce  
 Il core [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione architettura è basata su due file manifesto XML: un manifesto dell'applicazione e un manifesto di distribuzione. I file vengono utilizzati per descrivere in cui le applicazioni ClickOnce sono installate da, la modalità di aggiornamento e quando vengono aggiornate.  
  
### <a name="publishing-clickonce-applications"></a>Pubblicazione di applicazioni ClickOnce  
 Il manifesto dell'applicazione descrive l'applicazione stessa. Ciò include gli assembly, le dipendenze e i file che costituiscono l'applicazione, le autorizzazioni necessarie e il percorso in cui saranno disponibili aggiornamenti. Lo sviluppatore di applicazioni viene creato il manifesto dell'applicazione tramite la pubblicazione guidata di Visual Studio o la generazione e la modifica dello strumento (Mage.exe) nei [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Per ulteriori informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Il manifesto di distribuzione viene descritto come l'applicazione viene distribuita. Ciò include il percorso del manifesto dell'applicazione e la versione dell'applicazione in cui i client devono eseguire.  
  
### <a name="deploying-clickonce-applications"></a>Distribuzione di applicazioni ClickOnce  
 Dopo averlo creato, il manifesto di distribuzione viene copiato nel percorso di distribuzione. Può trattarsi di un server Web, condivisione file di rete o supporto, ad esempio un CD. In un percorso di distribuzione specificato nel manifesto di distribuzione verranno copiati anche il manifesto dell'applicazione e tutti i file dell'applicazione. Può essere lo stesso come il percorso di distribuzione, o può essere un percorso diverso. Quando si utilizza il **pubblicazione guidata** in Visual Studio, le operazioni di copia vengono eseguite automaticamente.  
  
### <a name="installing-clickonce-applications"></a>Installazione di applicazioni ClickOnce  
 Dopo la distribuzione nel percorso di distribuzione, gli utenti finali possono scaricare e installare l'applicazione facendo clic su un'icona che rappresenta il file manifesto di distribuzione in una pagina Web o in una cartella. Nella maggior parte dei casi, l'utente finale viene visualizzata una finestra di dialogo che chiede all'utente di confermare l'installazione, dopo l'installazione viene eseguita e l'applicazione viene avviata senza intervento aggiuntivo. Nei casi in cui l'applicazione richiede autorizzazioni elevate o se l'applicazione non è firmato da un certificato attendibile, la finestra di dialogo inoltre chiesto di concedere l'autorizzazione prima di poter continuare l'installazione. Sebbene ClickOnce installa per utente, l'elevazione delle autorizzazioni potrebbe essere necessario se esistono prerequisiti che richiedono privilegi di amministratore. Per ulteriori informazioni sulle autorizzazioni elevate, vedere [protezione delle applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Certificati possono essere considerati attendibili a livello di computer o enterprise, in modo che sia firmate con un certificato attendibile di applicazioni ClickOnce è possono installare automaticamente. Per ulteriori informazioni sui certificati attendibili, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).  
  
 L'applicazione può essere aggiunta all'utente **avviare** menu e di ottenere il **Aggiungi / Rimuovi programmi** gruppo il **Pannello di controllo**. A differenza di altre tecnologie di distribuzione, viene aggiunto nulla al **programmi** cartella o il Registro di sistema e diritti amministrativi non sono necessari per l'installazione  
  
> [!NOTE]
>  È anche possibile impedire l'applicazione venga aggiunto il **avviare** menu e **Aggiungi / Rimuovi programmi** gruppo, in effetti esattamente come un'applicazione Web. Per altre informazioni, vedere [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Aggiornamento di applicazioni ClickOnce  
 Quando gli sviluppatori di applicazioni creano una versione aggiornata dell'applicazione, che genera un nuovo manifesto dell'applicazione e copiare i file in un percorso di distribuzione, in genere una cartella di pari livello nella cartella di distribuzione dell'applicazione originale. L'amministratore aggiorna il manifesto di distribuzione in modo che punti al percorso della nuova versione dell'applicazione.  
  
> [!NOTE]
>  Il **pubblicazione guidata** in Visual Studio può essere utilizzato per eseguire questi passaggi.  
  
 Oltre al percorso di distribuzione, il manifesto di distribuzione contiene anche un percorso di aggiornamento (una condivisione file pagina Web o di rete) in cui viene controllata per le versioni aggiornate. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]**Pubblica** proprietà vengono utilizzate per specificare quando e con quale frequenza controllare la disponibilità di aggiornamenti. Comportamento di aggiornamento può essere specificato nel manifesto di distribuzione o può essere presentata come scelte dell'utente nell'interfaccia utente dell'applicazione mediante il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API. Inoltre, **pubblica** proprietà possono essere utilizzate per rendere gli aggiornamenti obbligatori o eseguire il rollback a una versione precedente. Per ulteriori informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Programmi di installazione di terze parti  
 È possibile personalizzare il programma di installazione ClickOnce per installare i componenti di terze parti insieme all'applicazione. È necessario disporre del package ridistribuibile (file .exe o file con estensione msi) e descrivono il pacchetto con un manifesto del prodotto indipendente dalla lingua e un manifesto di pacchetto specifico della lingua. Per ulteriori informazioni, vedere [la creazione di pacchetti del programma di avvio](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Strumenti di ClickOnce  
 La tabella seguente illustra gli strumenti che è possibile utilizzare per generare, modificare, firmare e firmare nuovamente i manifesti dell'applicazione e distribuzione.  
  
|Strumento|Descrizione|  
|----------|-----------------|  
|[Pagina Sicurezza, Creazione progetti](../ide/reference/security-page-project-designer.md)|Firma i manifesti dell'applicazione e distribuzione.|  
|[Pagina Pubblica, Creazione progetti](../ide/reference/publish-page-project-designer.md)|Genera l'errore e modificare i manifesti dell'applicazione e di distribuzione per le applicazioni Visual Basic e Visual c#.|  
|[Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Genera i manifesti dell'applicazione e di distribuzione per le applicazioni Visual Basic, Visual c# e Visual C++.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e distribuzione.<br /><br /> Può essere eseguito dal prompt dei comandi e script di batch.|  
|[MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Genera l'errore e modificare i manifesti dell'applicazione e di distribuzione.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e distribuzione.|  
|[Attività GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)|Genera il manifesto dell'applicazione.<br /><br /> Può essere eseguito da MSBuild. Per ulteriori informazioni, vedere [di riferimento su MSBuild](../msbuild/msbuild-reference.md).|  
|[Attività GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)|Genera il manifesto di distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per ulteriori informazioni, vedere [di riferimento su MSBuild](../msbuild/msbuild-reference.md).|  
|[Attività SignFile](../msbuild/signfile-task.md)|Firma i manifesti dell'applicazione e distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per ulteriori informazioni, vedere [di riferimento su MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Sviluppare un'applicazione personalizzata per generare i manifesti dell'applicazione e distribuzione.|  
  
 La tabella seguente illustra la versione di .NET Framework necessaria per supportare le applicazioni ClickOnce in questi browser.  
  
|Browser|Versione di .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione ClickOnce in Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Distribuzione di componenti COM con ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Compilazione di applicazioni ClickOnce dalla riga di comando](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Debug di applicazioni ClickOnce in cui si usa System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)