---
title: 'Procedura: utilizzare ClickOnce per distribuire applicazioni eseguibili su più versioni di .NET Framework | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c05d1317c2b8040baf23c98cff8a032f14f47798
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Procedura: utilizzare ClickOnce per distribuire applicazioni eseguibili in più versioni di .NET Framework
È possibile distribuire un'applicazione destinata a più versioni di .NET Framework tramite la tecnologia di distribuzione ClickOnce. Questo è necessario generare e aggiornare i manifesti dell'applicazione e distribuzione.  
  
> [!NOTE]
>  Prima di modificare l'applicazione di più versioni di .NET Framework di destinazione, è necessario assicurarsi che l'applicazione viene eseguita con più versioni di .NET Framework. Versione di common language runtime è diverso tra [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] rispetto a .NET Framework 2.0, .NET Framework 3.0 e 3.5 di .NET Framework.  
  
 Questo processo richiede i passaggi seguenti:  
  
1.  Generare i manifesti dell'applicazione e distribuzione.  
  
2.  Modificare il manifesto di distribuzione per elencare le diverse versioni di .NET Framework.  
  
3.  Modificare il file app. config per elencare le versioni di runtime di .NET Framework compatibile.  
  
4.  Modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti come assembly .NET Framework.  
  
5.  Firmare il manifesto dell'applicazione.  
  
6.  Aggiornare e firmare il manifesto di distribuzione.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Per generare i manifesti dell'applicazione e distribuzione  
  
-   Utilizzare la pubblicazione guidata o la pagina di pubblicazione di progettazione per pubblicare l'applicazione e generare l'applicazione e i file manifesto di distribuzione. Per ulteriori informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) o [pagina pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Per modificare il manifesto di distribuzione per elencare le diverse versioni di .NET Framework  
  
1.  Nella directory di pubblicazione, aprire il manifesto di distribuzione utilizzando l'Editor XML in Visual Studio. Il manifesto di distribuzione ha l'estensione Application.  
  
2.  Sostituire il codice XML tra i `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` e `</compatibleFrameworks>` elementi XML che elenca le versioni di .NET Framework supportate per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune versioni di .NET Framework disponibili e il codice XML di corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione di .NET Framework|XML|  
    |----------------------------|---------|  
    |Client 4|\<Framework targetVersion = "4.0" profile = supportedRuntime "Client" = "4.0.30319" / >|  
    |4 full|\<Framework targetVersion = "4.0" profile = supportedRuntime "Completo" = "4.0.30319" / >|  
    |3.5 client|\<Framework targetVersion = "3.5" profile = supportedRuntime "Client" = "2.0.50727" / >|  
    |3.5 completo|\<Framework targetVersion = "3.5" profile = supportedRuntime "Completo" = "2.0.50727" / >|  
    |3.0|\<Framework targetVersion = supportedRuntime "3.0" = "2.0.50727" / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Per modificare il file app. config per elencare le versioni di runtime di .NET Framework compatibile  
  
1.  In Esplora soluzioni, aprire il file app. config utilizzando l'Editor XML in Visual Studio.  
  
2.  Sostituire il codice XML tra (o aggiungere) il `<startup>` e `</startup>` elementi XML che elenca i runtime di .NET Framework supportati per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune versioni di .NET Framework disponibili e il codice XML di corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione di runtime di .NET framework|XML|  
    |------------------------------------|---------|  
    |Client 4|\<versione supportedRuntime = sku "v4.0.30319" = ". NETFramework, versione Version=v4.0, Profile = Client "/ >|  
    |4 full|\<versione supportedRuntime = sku "v4.0.30319" = ". NETFramework, versione = v4.0 "/ >|  
    |3.5 completo|\<version="v2.0.50727"/ supportedRuntime >|  
    |3.5 client|\<versione supportedRuntime = sku "v2.0.50727" = "Client" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Per modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti come assembly .NET Framework  
  
1.  Nella directory di pubblicazione, aprire il manifesto dell'applicazione utilizzando l'Editor XML in Visual Studio. Il manifesto di distribuzione ha l'estensione manifest.  
  
2.  Aggiungere `group="framework"` alla dipendenza XML per gli assembly sentinel (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, e `System.Data.Entity`). Ad esempio, il codice XML dovrebbe essere simile al seguente:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Aggiornare il numero di versione di `<assemblyIdentity>` elemento per Microsoft.Windows.CommonLanguageRuntime al numero di versione di .NET Framework che è il minimo comune denominatore. Ad esempio, se l'applicazione è destinata a .NET Framework 3.5 e [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], utilizzare il 2.0.50727.0 numero di versione e il codice XML dovrebbe essere simile al seguente:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Per aggiornare e firmare nuovamente l'applicazione e distribuzione di manifesti  
  
-   Aggiornare e firmare nuovamente i manifesti dell'applicazione e distribuzione. Per altre informazioni, vedere [Procedura: ripetere la firma dei manifesti dell'applicazione e di distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md)   
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Schema dei file di configurazione](/dotnet/framework/configure-apps/file-schema/index)