---
title: '&lt;distribuzione&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: "30"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 0caff13f84208152b3fa2ff4e56a7a2c7f0b6dd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;distribuzione&gt; elemento (distribuzione di ClickOnce)
Identifica gli attributi usati per la distribuzione degli aggiornamenti e l'esposizione al sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `deployment` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1`. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`install`|Obbligatorio. Specifica se l'applicazione definisce una presenza di Windows **avviare** menu e nel Pannello di controllo **Aggiungi / Rimuovi programmi** dell'applicazione. I valori validi sono `true` e `false`. Se `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eseguirà sempre la versione più recente dell'applicazione dalla rete e non riconosce il `subscription` elemento.|  
|`minimumRequiredVersion`|Facoltativo. Specifica la versione minima dell'applicazione che è possibile eseguire sul client. Se il numero di versione dell'applicazione è inferiore al numero di versione specificato nel manifesto di distribuzione, l'applicazione non verrà eseguita. Numeri di versione devono essere specificati nel formato `N.N.N.N`, dove `N` è un intero senza segno. Se il `install` attributo `false`, `minimumRequiredVersion` non deve essere impostato.|  
|`mapFileExtensions`|Facoltativo. Il valore predefinito è `false`. Se `true`, tutti i file nella distribuzione devono avere l'estensione. deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]rimuoverà questa estensione questi file come download dal server Web. Se si pubblica l'applicazione utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], questa estensione aggiunta automaticamente a tutti i file. Questo parametro consente di tutti i file all'interno di un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione per essere scaricato da un server Web che impedisce la trasmissione dei file che terminano con "unsafe" estensioni, ad esempio .exe.|  
|`disallowUrlActivation`|Facoltativo. Il valore predefinito è `false`. Se `true`, impedisce a un'applicazione installata facendo clic sull'URL o immettendo l'URL in Internet Explorer in corso l'avvio. Se il `install` attributo non è presente, questo attributo viene ignorato.|  
|`trustURLParameters`|Facoltativo. Il valore predefinito è `false`. Se `true`, l'URL può contenere parametri di stringa di query che vengono passati all'applicazione, molto simili argomenti della riga di comando vengono passati a un'applicazione della riga di comando. Per ulteriori informazioni, vedere [procedura: recuperare le informazioni di stringa di Query in un'applicazione ClickOnce Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Se il `disallowUrlActivation` attributo `true`, `trustUrlParameters` deve essere escluso dal manifesto o impostata esplicitamente su `false`.|  
  
 Il `deployment` elemento contiene anche gli elementi figlio seguenti.  
  
## <a name="subscription"></a>Sottoscrizione  
 Facoltativo. Contiene il `update` elemento. Il `subscription` elemento non ha attributi. Se il `subscription` elemento non esiste, il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione mai analizzi gli aggiornamenti. Se il `install` attributo del `deployment` elemento è `false`, `subscription` elemento viene ignorato, poiché un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che viene sempre avviata dalla rete utilizza la versione più recente.  
  
## <a name="update"></a>aggiorna  
 Obbligatorio. Questo è un elemento figlio del `subscription` elemento e può essere il `beforeApplicationStartup` o `expiration` elemento. `beforeApplicationStartup`e `expiration` non possono essere specificati nel manifesto di distribuzione stessa.  
  
 Il `update` elemento non ha attributi.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Facoltativo. Questo è un elemento figlio del `update` elemento e non ha attributi. Quando il `beforeApplicationStartup` elemento esiste, l'applicazione sarà bloccato quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] controlla gli aggiornamenti, se il client è online. Se questo elemento non esiste, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] innanzitutto analizzi gli aggiornamenti in base ai valori specificati per il `expiration` elemento. `beforeApplicationStartup`e `expiration` non possono essere specificati nel manifesto di distribuzione stessa.  
  
## <a name="expiration"></a>scadenza  
 Facoltativo. Questo è un elemento figlio del `update` elemento, e non ha elementi figlio. `beforeApplicationStartup`e `expiration` non possono essere specificati nel manifesto di distribuzione stessa. Quando si verifica la disponibilità di aggiornamenti e viene rilevata una versione aggiornata, la nuova versione memorizza nella cache mentre è in esecuzione la versione esistente. Installa al successivo avvio della nuova versione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
 Il `expiration` elemento supporta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`maximumAge`|Obbligatorio. Identifica come precedente dovrebbe diventare l'aggiornamento corrente prima che l'applicazione esegue un controllo di aggiornamento. L'unità di tempo è determinata dal `unit` attributo.|  
|`unit`|Obbligatorio. Identifica l'unità di tempo per `maximumAge`. Le unità valide sono `hours`, `days`, e `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Per .NET Framework 2.0, questo elemento è obbligatorio se il manifesto di distribuzione contiene un `subscription` sezione. Per .NET Framework 3.5 e versioni successive, questo elemento è facoltativo e utilizzerà il server e il percorso di file in cui è stato individuato il manifesto di distribuzione.  
  
 Questo elemento è figlio dell'elemento `deployment` e ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`codebase`|Obbligatorio. Identifica il percorso del manifesto di distribuzione che viene utilizzato per aggiornare, come un identificatore URI (Uniform Resource), il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Questo elemento consente inoltre di percorsi di aggiornamento per le installazioni basate sul CD di inoltro. Deve essere un URI valido.|  
  
## <a name="remarks"></a>Note  
 È possibile configurare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione per analizzare gli aggiornamenti all'avvio, cercare gli aggiornamenti dopo l'avvio o non controllare mai gli aggiornamenti. Per analizzare gli aggiornamenti all'avvio, assicurarsi che il `beforeApplicationStartup` elemento esiste nel `update` elemento. Per eseguire la scansione degli aggiornamenti dopo l'avvio, assicurarsi che il `expiration` elemento esiste nel `update` elemento e che siano stati specificati gli intervalli di aggiornamento.  
  
 Per disabilitare il controllo degli aggiornamenti, rimuovere il `subscription` elemento. Quando si specifica nel manifesto di distribuzione per non analizzare mai gli aggiornamenti, eseguire manualmente è possibile verificare gli aggiornamenti tramite il <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metodo.  
  
 Per ulteriori informazioni sugli aggiornamenti di deploymentProvider, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio di codice seguente viene illustrato un `deployment` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione. Nell'esempio viene utilizzato un `deploymentProvider` elemento per indicare il percorso di aggiornamento preferito.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)