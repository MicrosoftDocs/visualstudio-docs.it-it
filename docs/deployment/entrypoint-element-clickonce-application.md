---
title: '&lt;punto di ingresso&gt; elemento (applicazione ClickOnce) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beb140a64a415ab1a42f8157e2fafb1d20f9569a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;punto di ingresso&gt; elemento (applicazione ClickOnce)
Identifica l'assembly che deve essere eseguito quando questa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene eseguita in un computer client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v2`. Potrebbe essere presente una sola `entryPoint` elemento definito in un manifesto dell'applicazione.  
  
 Il `entryPoint` elemento presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Facoltativo. Questo valore non è utilizzato da .NET Framework.|  
  
 `entryPoint` presenta gli elementi seguenti:  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Obbligatorio. Il ruolo di `assemblyIdentity` e relativi attributi è definito in [ \<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 Il `processorArchitecture` attributo di questo elemento e `processorArchitecture` attributo definito nella `assemblyIdentity` altrove nell'applicazione manifesto deve corrispondere.  
  
## <a name="commandline"></a>Riga di comando  
 Obbligatorio. Deve essere un figlio di `entryPoint` elemento. Non dispone di alcun elemento figlio e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`file`|Obbligatorio. Un riferimento locale all'assembly di avvio per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Questo valore non può contenere una barra (/) o una barra rovesciata (\\) separatori del percorso.|  
|`parameters`|Obbligatorio. Descrive l'azione da intraprendere con il punto di ingresso. L'unico valore valido è `run`; se viene fornita una stringa vuota, `run` verrà utilizzato.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Facoltativo. Se incluso, specifica che la distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.  
  
 Se questo elemento è presente, il `assemblyIdentity` e `commandLine` elementi non possono essere presenti. In tal caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] genererà un errore di convalida durante l'installazione.  
  
 Questo elemento dispone di alcun attributo e nessun elemento figlio.  
  
## <a name="customux"></a>customUX  
 Facoltativo. Specifica che l'applicazione è installato e gestita da un programma di installazione personalizzato e non creare una voce di menu Start, scelta rapida o aggiungere o rimuovere la voce di programmi.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Un'applicazione che include l'elemento customUX deve fornire un programma di installazione personalizzato che utilizza il <xref:System.Deployment.Application.InPlaceHostingManager> classe per eseguire le operazioni di installazione. Un'applicazione con questo elemento non può essere installata facendo doppio clic sul relativo manifesto o setup.exe dei prerequisiti del programma di avvio. Il programma di installazione personalizzato è possibile creare voci di menu Start, collegamenti e voci Installazione applicazioni. Se il programma di installazione personalizzato non crea una voce in Installazione applicazioni, è necessario archiviare l'identificatore di sottoscrizione fornito dal <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> proprietà e consentono all'utente di disinstallare l'applicazione in un secondo momento chiamando la <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metodo. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Note  
 Questo elemento identifica l'assembly e punto di ingresso per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
 Non è possibile utilizzare `commandLine` per passare i parametri nell'applicazione in fase di esecuzione. Si può accedere ai parametri di stringa di query per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione dell'applicazione <xref:System.AppDomain>. Per ulteriori informazioni, vedere [procedura: recuperare le informazioni di stringa di Query in un'applicazione ClickOnce Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato un `entryPoint` elemento in un manifesto dell'applicazione per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Questo esempio di codice fa parte di un esempio più esaustivo disponibile per il [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md) argomento.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)