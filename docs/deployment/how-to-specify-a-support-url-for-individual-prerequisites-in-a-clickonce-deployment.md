---
title: 'Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4fe4deb04dbcc29a04036973d479803ee4667c5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce
Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] possibile testare la distribuzione per un numero di prerequisiti che devono essere disponibili nel computer client per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esecuzione dell'applicazione. Queste includono la versione minima richiesta del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la versione del sistema operativo e tutti gli assembly che devono essere preinstallati nella global assembly cache (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], tuttavia, non è possibile installare uno di questi prerequisiti stesso. Se non viene trovato un prerequisito, semplicemente arresta l'installazione e consente di visualizzare una finestra di dialogo che spiega il motivo per cui l'installazione non riuscita.  
  
 Esistono due metodi per l'installazione dei prerequisiti. È possibile installare mediante l'applicazione di avvio automatico. In alternativa, è possibile specificare un URL di supporto per i singoli prerequisiti, viene visualizzato agli utenti nella finestra di dialogo, se non viene trovato il prerequisito. La pagina a cui fa riferimento l'URL può contenere collegamenti a istruzioni per installare i prerequisiti richiesti. Se un'applicazione non specifica un URL di supporto per un singolo prerequisito [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visualizza l'URL di supporto specificato nel manifesto di distribuzione per l'applicazione nel suo complesso, se è definito.  
  
 Mentre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe e MageUI.exe possono essere utilizzate tutte per generare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzioni, nessuno di questi strumenti supporta direttamente la specifica di un URL di supporto per i singoli prerequisiti. Questo documento viene descritto come modificare la distribuzione manifesto dell'applicazione e distribuzione per includere gli URL di supporto.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Specificare un URL di supporto per un singolo prerequisito  
  
1.  Aprire il manifesto dell'applicazione (file. manifest) per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione in un editor di testo.  
  
2.  Per un prerequisito necessario per il sistema operativo, aggiungere il `supportUrl` attributo il `dependentOS` elemento:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Per un prerequisito per una determinata versione di common language runtime, aggiungere il `supportUrl` attributo la `dependentAssembly` voce che indica la dipendenza di common language runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Per un prerequisito per un assembly che deve essere preinstallato nella global assembly cache, impostare il `supportUrl` per il `dependentAssembly` elemento che specifica l'assembly richiesto:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Facoltativo. Per le applicazioni destinate a .NET Framework 4, aprire il manifesto di distribuzione (file con estensione Application) per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione in un editor di testo.  
  
6.  Per un prerequisito di .NET Framework 4, aggiungere il `supportUrl` attributo il `compatibleFrameworks` elemento:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Dopo aver modificato manualmente il manifesto dell'applicazione, è necessario firmare il manifesto dell'applicazione utilizzando il certificato digitale, quindi aggiornare e firmare nuovamente anche il manifesto di distribuzione. È necessario utilizzare il Mage.exe o MageUI.exe SDK di strumenti per eseguire questa attività, come la rigenerazione di questi file utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Cancella le modifiche manuali apportate. Per ulteriori informazioni sull'utilizzo di Mage.exe per firmare nuovamente i manifesti, vedere [procedura: firmare di nuovo Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Se l'applicazione è contrassegnata per l'esecuzione in attendibilità parziale, l'URL di supporto non viene visualizzata nella finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)