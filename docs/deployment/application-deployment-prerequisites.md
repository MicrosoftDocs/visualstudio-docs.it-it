---
title: Prerequisiti per la distribuzione di applicazioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: "51"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 4060933a904a5cb842a7c319b3ef5da645e4119e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="application-deployment-prerequisites"></a>Prerequisiti per la distribuzione dell'applicazione
Affinché l'applicazione venga installata ed eseguita correttamente, è necessario che nel computer di destinazione siano già installati tutti i componenti da cui l'applicazione dipende. Ad esempio, la maggior parte delle applicazioni create con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hanno una dipendenza da [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]; prima di installare l'applicazione, è necessario che nel computer di destinazione sia presente la versione corretta di Common Language Runtime.  
  
 È possibile selezionare questi prerequisiti di **la finestra di dialogo Prerequisiti** e installare .NET Framework e altri ridistribuibili come parte dell'installazione. Questa procedura è nota come *bootstrap*. Successivamente, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera un programma eseguibile denominato Setup.exe, noto anche come un *programma di avvio automatico*. Il programma di avvio automatico installa questi prerequisiti prima dell'esecuzione dell'applicazione. Per ulteriori informazioni sulla selezione di questi prerequisiti, vedere [la finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).  
  
 Ogni prerequisito è un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio automatico è un gruppo di directory e file che contengono i file manifesto in cui è descritto come deve essere installato il prerequisito. Se i prerequisiti dell'applicazione non figurano le **la finestra di dialogo Prerequisiti**, è possibile creare programmi di avvio automatico personalizzati e aggiungerli a Visual Studio. È quindi possibile selezionare i prerequisiti nel **la finestra di dialogo Prerequisiti**. Per ulteriori informazioni, vedere [la creazione di pacchetti del programma di avvio](../deployment/creating-bootstrapper-packages.md).  
  
 Per impostazione predefinita, il bootstrap è abilitato per la distribuzione ClickOnce. Il programma di avvio automatico generato per la distribuzione ClickOnce è firmato. È possibile disabilitare il bootstrap per un componente, ma è consigliabile procedere solo dopo avere verificato che in tutti i computer di destinazione sia già installata la versione corretta del componente.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Bootstrap e distribuzione ClickOnce  
 Prima di installare un'applicazione in un computer client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esaminerà il client per verificare che siano soddisfatti i requisiti specificati nel manifesto dell'applicazione, tra cui:  
  
-   Versione minima richiesta di Common Language Runtime, specificata come dipendenza di assembly nel manifesto dell'applicazione.  
  
-   Versione minima del sistema operativo Windows richiesta dall'applicazione, specificata nel manifesto dell'applicazione mediante l'elemento `<osVersionInfo>` (Vedere [ \<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md))  
  
-   Versione minima di tutti gli assembly che devono essere preinstallati nella Global Assembly Cache (GAC), specificata dalle dichiarazioni delle dipendenze degli assembly nel manifesto dell'assembly.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]in grado di rilevare i prerequisiti mancanti, ed è possibile installare i prerequisiti utilizzando un programma di avvio automatico. Per ulteriori informazioni, vedere [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Per modificare i valori nei manifesti generati da strumenti come [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e MageUI.exe, è necessario modificare il manifesto dell'applicazione in un editor di testo, quindi firmare nuovamente sia il manifesto dell'applicazione che quello della distribuzione. Per ulteriori informazioni, vedere [procedura: firmare di nuovo Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Se si usa Visual Studio e ClickOnce per distribuire l'applicazione, i pacchetti del programma di avvio automatico selezionati per impostazione predefinita variano a seconda della versione di .NET Framework inclusa nella soluzione. Tuttavia, se si modifica la versione di .NET Framework di destinazione, è necessario aggiornare le opzioni di **la finestra di dialogo Prerequisiti** manualmente.  
  
|.NET Framework di destinazione|Pacchetti del programma di avvio automatico selezionati|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 Con la distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la pagina Publish.htm generata mediante la Pubblicazione guidata di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] punta a un collegamento per l'installazione della sola applicazione o a un collegamento per l'installazione sia dell'applicazione che dei componenti avviati automaticamente.  
  
 Se il programma di avvio automatico viene generato mediante la Pubblicazione guidata ClickOnce o la pagina di pubblicazione in Visual Studio, il file Setup.exe è firmato automaticamente. Se invece si preferisce usare il certificato del cliente per firmare il programma di avvio automatico, è possibile firmare il file in un secondo momento.  
  
## <a name="bootstrapping-and-msbuild"></a>Bootstrap e MSBuild  
 Se non si usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ma le applicazioni vengono compilate dalla riga di comando, l'applicazione di avvio automatico [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può essere creata mediante un'attività di Microsoft Build Engine (MSBuild). Per ulteriori informazioni, vedere [GenerateBootstrapper (attività)](../msbuild/generatebootstrapper-task.md).  
  
 In alternativa al bootstrap, è possibile pre-distribuire i componenti mediante un sistema elettronico di distribuzione del software, ad esempio Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argomenti della riga di comando per il programma di avvio automatico (Setup.exe)  
 Il file Setup.exe generato da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e dalle attività di MSBuild supporta il piccolo set di argomenti della riga di comando indicato di seguito. Gli eventuali altri argomenti forniti all'applicazione di bootstrap vengono inoltrati al programma di installazione dell'applicazione.  
  
 Se si modifica una qualsiasi opzione del programma di avvio automatico, è necessario modificare il programma di avvio automatico non firmato, quindi firmare il relativo file in un secondo momento.  
  
|Argomento della riga di comando|Descrizione|  
|---------------------------|-----------------|  
|**-?, -h, - Guida**|Visualizza una finestra di dialogo della Guida.|  
|**-url - componentsurl**|Visualizza l'URL archiviato e l'URL dei componenti per questa configurazione.|  
|**-url =**`location`|Imposta l'URL in cui Setup.exe cercherà l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|  
|**-componentsurl =**`location`|Imposta l'URL in cui Setup.exe cercherà le dipendenze, ad esempio [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|**-homesite =** `true` **&#124;**`false`|Quando `true`, le dipendenze vengono scaricate dal percorso preferito sul sito del fornitore. Esegue l'override di **- componentsurl** impostazione. Quando `false`, le dipendenze vengono scaricate dall'URL specificato da **- componentsurl**.|  
  
## <a name="operating-system-support"></a>Supporto del sistema operativo  
 Il programma di avvio automatico di Visual Studio non è supportato in Windows Server 2008 Server Core o Windows Server 2008 R2 Server Core, che forniscono un ambiente server a bassa manutenzione con funzionalità limitate. Ad esempio, l'opzione di installazione dei componenti di base del server supporta esclusivamente il profilo .NET Framework 3.5 Server Core, quindi non è possibile eseguire le funzionalità di Visual Studio che dipendono dalla versione completa di .NET Framework.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)