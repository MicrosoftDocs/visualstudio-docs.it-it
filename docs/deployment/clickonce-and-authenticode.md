---
title: ClickOnce e Authenticode | Documenti Microsoft
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
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: aa1ab7ac947a5fbdf9d0423c57a987a4ffe8be97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-and-authenticode"></a>ClickOnce e Authenticode
*Authenticode* è una tecnologia Microsoft basata sulla crittografia standard che consente di firmare il codice di un'applicazione con certificati digitali che verificano l'autenticità dell'editore dell'applicazione. Usando la tecnologia Authenticode per la distribuzione di applicazioni, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente di ridurre i rischi di trojan horse, ovvero virus o altri programmi dannosi presentati da una terza parte malintenzionata in modo ingannevole come programmi legittimi provenienti da una fonte definita e attendibile. Firmare le distribuzioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con un certificato digitale è un passaggio facoltativo per verificare che gli assembly e i file non siano stati manomessi.  
  
 Le sezioni seguenti descrivono i diversi tipi di certificati digitali usati in Authenticode, la procedura di convalida dei certificati mediante Autorità di certificazione (CA, Certification Authority), il ruolo del timestamp nei certificati e i metodi di archiviazione disponibili per i certificati.  
  
## <a name="authenticode-and-code-signing"></a>Firma del codice e Authenticode  
 Un *certificato digitale* è un file che contiene una coppia di chiavi di crittografia pubblica/privata, nonché i metadati relativi all'editore a cui è stato rilasciato il certificato e all'autorità di certificazione.  
  
 Esistono vari tipi di certificati Authenticode. Ogni certificato viene configurato per diversi tipi di firma. Per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è necessario avere un certificato Authenticode valido per la firma del codice. Se si prova a firmare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con un altro tipo di certificato, ad esempio un certificato di posta elettronica digitale, l'applicazione non funzionerà. Per altre informazioni, vedere [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=179452)(Introduzione alla firma del codice).  
  
 È possibile ottenere un certificato per la firma del codice in uno dei tre modi seguenti:  
  
-   Acquistandone uno da un fornitore di certificati.  
  
-   Ricevendone uno da un gruppo dell'organizzazione responsabile della creazione di certificati digitali.  
  
-   Generare un certificato personalizzato mediante il cmdlet PowerShell New-SelfSignedCertificate o MakeCert.exe, che è incluso il [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Vantaggi derivanti dall'uso di Autorità di certificazione  
 Un certificato generato tramite New-SelfSignedCertificate o l'utilità MakeCert.exe in genere viene chiamato un *autocertificato* o *test cert*. Questo tipo di certificato agisce in modo analogo ai file con estensione snk in .NET Framework. È costituito esclusivamente da una coppia di chiavi crittografiche pubbliche/private e non contiene informazioni verificabili sull'editore. Gli autocertificati consentono di distribuire applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con un elevato livello di attendibilità in una rete intranet. Tuttavia, quando sono eseguite in un computer client, queste applicazioni vengono identificate da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] come provenienti da un editore sconosciuto. Per impostazione predefinita, non è possibile usare la distribuzione di applicazioni attendibili per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] firmate con autocertificati e distribuite su Internet.  
  
 Al contrario, se si riceve un certificato proveniente da una CA, ad esempio un fornitore di certificati o un reparto dell'organizzazione, il certificato offre maggiore sicurezza agli utenti. Non solo identifica l'editore del software firmato, ma verifica anche l'identità mediante un controllo con la CA che ha apposto la firma. Se la CA non è l'autorità radice, Authenticode verificherà con l'autorità radice che la CA sia autorizzata a rilasciare certificati. Per maggiore sicurezza, si consiglia di usare un certificato rilasciato da una CA, se possibile.  
  
 Per ulteriori informazioni sulla generazione di certificati autofirmati, vedere [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) o [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
### <a name="timestamps"></a>Timestamp  
 I certificati usati per firmare applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scadono dopo un determinato periodo di tempo, in genere dodici mesi. Per evitare di dover firmare costantemente le stesse applicazioni con nuovi certificati, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supporta i timestamp. Se un'applicazione è firmata con un timestamp, il certificato continuerà a essere accettato anche dopo la scadenza, purché il timestamp sia valido. Questo consente il download e l'esecuzione delle applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con certificati scaduti ma timestamp validi. Permette anche di continuare a scaricare e installare gli aggiornamenti per le applicazioni installate con certificati scaduti.  
  
 Per includere un timestamp in un server applicazioni, deve essere disponibile un server di timestamp. Per informazioni sulla selezione di un server di timestamp, vedere [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Aggiornamento di certificati scaduti  
 Nelle versioni precedenti di .NET Framework, l'aggiornamento di un'applicazione con certificato scaduto può determinare l'interruzione dell'applicazione stessa. Per risolvere il problema, usare uno dei metodi seguenti:  
  
-   Aggiornare .NET Framework alla versione 2.0 SP1 o successiva su Windows XP oppure alla versione 3.5 o successiva su Windows Vista.  
  
-   Disinstallare l'applicazione e reinstallare una nuova versione con un certificato valido.  
  
-   Creare un assembly della riga di comando che aggiorna il certificato. Nell' [articolo del Supporto tecnico Microsoft 925521](http://go.microsoft.com/fwlink/?LinkId=179454)sono disponibili informazioni dettagliate su questa procedura.  
  
### <a name="storing-certificates"></a>Archiviazione dei certificati  
  
-   È possibile archiviare i certificati nel file system, come file con estensione pfx, oppure all'interno di un contenitore di chiavi. Un utente su un dominio Windows può avere più contenitori di chiavi. Per impostazione predefinita, l'utilità MakeCert.exe archivia i certificati nel contenitore di chiavi personale, a meno che non venga specificato di salvarli in un file con estensione pfx. Mage.exe e MageUI.exe, gli strumenti di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] per la creazione di distribuzioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , consentono di usare certificati archiviati in entrambi i modi.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)