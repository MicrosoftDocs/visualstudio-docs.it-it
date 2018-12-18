---
title: Cenni preliminari sulla distribuzione di applicazioni attendibili | Documenti Microsoft
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
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: "31"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 34e83d6b035ba6ea91190fa89b9e1a63366e7907
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="trusted-application-deployment-overview"></a>Cenni preliminari sulla distribuzione di applicazioni attendibili
Questo argomento presenta informazioni generali su come distribuire applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con autorizzazioni elevate usando la tecnologia per la distribuzione di applicazioni attendibili.  
  
 La distribuzione di applicazioni attendibili, parte della tecnologia di distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , consente alle organizzazioni di qualsiasi dimensione di concedere autorizzazioni aggiuntive a un'applicazione gestita in modo più sicuro senza richieste dell'utente. Con la distribuzione di applicazioni attendibili, un'organizzazione può configurare semplicemente un computer client in modo che disponga di un elenco di editori attendibili, identificati usando i certificati Authenticode. In seguito, tutte le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] firmate da uno di questi editori attendibili ricevono un livello di attendibilità superiore.  
  
> [!NOTE]
>  La distribuzione di applicazioni attendibili richiede una configurazione eseguita una sola volta nel computer di un utente. Negli ambienti desktop gestiti, questa configurazione può essere eseguita usando i criteri globali. Se non è la soluzione desiderata per l'applicazione, usare l'elevazione delle autorizzazioni. Per altre informazioni, vedere [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="trusted-application-deployment-basics"></a>Nozioni fondamentali sulla distribuzione di applicazioni attendibili  
 La tabella seguente mostra gli oggetti e i ruoli coinvolti nella distribuzione di applicazioni attendibili.  
  
|Oggetto o ruolo|Descrizione|  
|--------------------|-----------------|  
|amministratore|Entità dell'organizzazione responsabile dell'aggiornamento e della gestione dei computer client|  
|gestore di attendibilità|Sottosistema all'interno di Common Language Runtime (CLR) responsabile dell'applicazione della sicurezza delle applicazioni client.|  
|publisher|Entità che scrive e gestisce l'applicazione.|  
|deployer|Entità che crea pacchetti e distribuisce l'applicazione agli utenti.|  
|certificato|Firma crittografica formata da una chiave pubblica e da una privata. In genere viene emessa da un'autorità di certificazione (CA) che ne garantisce l'autenticità.|  
|certificato Authenticode|Certificato con metadati incorporati che descrive, tra le altre cose, i possibili usi del certificato.|  
|autorità di certificazione|Organizzazione che verifica l'identità degli editori ed emette certificati incorporati nei metadati dell'editore.|  
|autorità radice|Autorità di certificazione che autorizza altre autorità di certificazione a emettere certificati.|  
|contenitore di chiavi|Spazio di archiviazione logico in Microsoft Windows per l'archiviazione dei certificati.|  
|editori attendibili|Editore il cui certificato Authenticode è stato aggiunto a un elenco scopi consentiti ai certificati (CTL) in un computer client.|  
  
 Nelle organizzazioni più grandi, l'editore e il deployer sono in genere due entità separate:  
  
-   L'editore è il gruppo che crea l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .  
  
-   Il deployer è il gruppo, in genere del reparto IT, che distribuisce l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ai computer desktop aziendali.  
  
 Attenersi alla seguente procedura per sfruttare i vantaggi della distribuzione di applicazioni attendibili:  
  
1.  Ottenere un certificato per l'editore.  
  
2.  Aggiungere l'editore all'archivio Editori attendibili in tutti i client.  
  
3.  Creare l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .  
  
4.  Firmare il manifesto della distribuzione con il certificato dell'editore.  
  
5.  Pubblicare la distribuzione dell'applicazione nei computer client.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Ottenere un certificato per l'editore  
 I certificati digitali sono un componente principale del sistema di sicurezza e autenticazione Microsoft Authenticode. Authenticode è una parte standard del sistema operativo Windows. Tutte le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] devono essere firmate con un certificato digitale, a prescindere se partecipano alla distribuzione di applicazioni attendibili. Per una spiegazione completa di come funziona Authenticode con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Aggiungere l'editore all'archivio Editori attendibili  
 Affinché l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] riceva un livello di attendibilità superiore, è necessario aggiungere il certificato come editore attendibile a ogni computer client in cui verrà eseguita l'applicazione. Si tratta di una configurazione che si esegue una sola volta. Dopo il completamento, è possibile distribuire tutte le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] firmate con il certificato editore desiderate, che verranno eseguite con un livello di attendibilità elevato.  
  
 Se si distribuisce l'applicazione in un ambiente desktop gestito, ad esempio una Intranet aziendale che esegue il sistema operativo Windows, è possibile aggiungere gli editori attendibili a un archivio del client creando un nuovo elenco scopi consentiti ai certificati (CTL) con Criteri di gruppo. Per altre informazioni, vedere [Create a certificate trust list for a Group Policy object](http://go.microsoft.com/fwlink/?LinkId=102576)(Creare un elenco scopi consentiti ai certificati per un oggetto Criteri di gruppo).  
  
 Se non si distribuisce l'applicazione in un ambiente desktop gestito, sono disponibili le seguenti opzioni per aggiungere un certificato all'archivio Editori attendibili:  
  
-   Spazio dei nomi <xref:System.Security.Cryptography?displayProperty=fullName> .  
  
-   CertMgr.exe, che è un componente di Internet Explorer e pertanto è presente in Windows 98 e tutte le versioni successive. Per ulteriori informazioni, vedere [Certmgr.exe (strumento di gestione certificati)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).  
  
### <a name="create-a-clickonce-application"></a>Creare un'applicazione ClickOnce  
 Un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è un'applicazione client [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] combinata con file manifesto che descrivono l'applicazione e forniscono i parametri di installazione. È possibile convertire il programma in applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usando il comando **Publish** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In alternativa, è possibile generare tutti i file richiesti per la distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usando gli strumenti inclusi in [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Per ulteriori informazioni su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 La distribuzione di applicazioni attendibili è specifica per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]è può essere usata solo con le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .  
  
### <a name="sign-the-deployment"></a>Formare la distribuzione  
 Dopo aver ottenuto il certificato, usarlo per firmare la distribuzione. Se si distribuisce l'applicazione usando la pubblicazione guidata di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , viene generato automaticamente un certificato di prova se non è già stato specificato un altro certificato. Tuttavia, è anche possibile usare la finestra Creazione progetti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per specificare un certificato fornito da un'autorità di certificazione.  Vedere anche [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata] (http://msdn.microsoft.com/library/31kztyey\(v=vs.110\).  
  
> [!CAUTION]
>  Non si consiglia di distribuire l'applicazione con un certificato di prova.  
  
 È anche possibile firmare l'applicazione usando gli strumenti SDK Mage.exe o MageUI.exe. Per ulteriori informazioni, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Per un elenco completo delle opzioni della riga di comando relative alla firma della distribuzione, vedere [Mage.exe (generazione manifesto e lo strumento di modifica)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
### <a name="publish-the-application"></a>Pubblicare l'applicazione  
 Dopo aver firmato i manifesti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , l'applicazione è pronta per la pubblicazione nel percorso di installazione. Il percorso di installazione può essere un server Web, una condivisione file o il disco locale. Quando un client accede al manifesto della distribuzione per la prima volta, il gestore di attendibilità deve determinare se all'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono state concesse le autorizzazioni per l'esecuzione con un livello di trust superiore da un editore attendibile installato. Per effettuare questa scelta, il gestore di attendibilità confronta il certificato usato per firmare la distribuzione con i certificati archiviati nell'archivio Editori attendibili del client. Se il gestore di attendibilità trova una corrispondenza, l'applicazione viene eseguita con un livello di attendibilità elevato.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Distribuzione di applicazioni attendibili ed elevazione delle autorizzazioni  
 Se l'editore corrente non è attendibile, il gestore di attendibilità usa l'elevazione delle autorizzazioni per chiedere all'utente se desidera concedere le autorizzazioni elevate all'applicazione. Se l'elevazione delle autorizzazioni è stata disabilitata dall'amministratore, tuttavia, l'applicazione non riesce a ottenere le autorizzazioni per l'esecuzione. L'applicazione non viene eseguita e l'utente non visualizza alcuna notifica. Per ulteriori informazioni sull'elevazione delle autorizzazioni, vedere [protezione delle applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Limitazioni della distribuzione di applicazioni attendibili  
 È possibile usare la distribuzione di applicazioni attendibili per concedere un livello di attendibilità elevato alle applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuite tramite Web o tramite una condivisione file aziendale. Non è necessario usare la distribuzione di applicazioni attendibili per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuite con un CD perché, per impostazione predefinita, a queste applicazioni viene concessa l'attendibilità totale.  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
