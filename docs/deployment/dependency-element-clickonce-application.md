---
title: '&lt;dipendenza&gt; elemento (applicazione ClickOnce) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 7c3319661a4c0df298cd844c4d71c6855cad818c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;dipendenza&gt; elemento (applicazione ClickOnce)
Identifica una dipendenza di piattaforma o un assembly che è necessaria per l'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `dependency` elemento è obbligatorio. Possono esistere più istanze di `dependency` nel manifesto dell'applicazione stessa.  
  
 Il `dependency` elemento non ha attributi e contiene gli elementi figlio seguenti.  
  
### <a name="dependentos"></a>dependentOS  
 Facoltativo. Contiene il `osVersionInfo` elemento. Il `dependentOS` e `dependentAssembly` elementi si escludono a vicenda: uno o l'altro deve esistere per un `dependency` elemento, ma non entrambi.  
  
 `dependentOS`supporta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`supportUrl`|Facoltativo. Specifica un URL di supporto per la piattaforma dipendente. L'URL viene visualizzato all'utente se viene trovata la piattaforma richiesta.|  
|`description`|Facoltativo. Descrive, in forma leggibile, il sistema operativo specificato per il `dependentOS` elemento.|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentOS` e contiene l'elemento `os`. Questo elemento non ha attributi.  
  
### <a name="os"></a>sistema operativo  
 Obbligatorio. Questo elemento è figlio dell'elemento `osVersionInfo`. Questo elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`majorVersion`|Obbligatorio. Specifica il numero di versione principale del sistema operativo.|  
|`minorVersion`|Obbligatorio. Specifica il numero di versione secondaria del sistema operativo.|  
|`buildNumber`|Obbligatorio. Specifica il numero di build del sistema operativo.|  
|`servicePackMajor`|Obbligatorio. Specifica il numero principale del service pack del sistema operativo.|  
|`servicePackMinor`|Facoltativo. Specifica il numero secondario del service pack del sistema operativo.|  
|`productType`|Facoltativo. Identifica il valore del tipo di prodotto. I valori validi sono `server`, `workstation` e `domainController`. Ad esempio, per Windows 2000 Professional, il valore dell'attributo è `workstation`.|  
|`suiteType`|Facoltativo. Identifica una famiglia di prodotti disponibile nel sistema o il tipo di configurazione del sistema. I valori validi sono `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, e `terminal`. Ad esempio, per Windows 2000 Professional, il valore dell'attributo è `professional`.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 Facoltativo. Contiene il `assemblyIdentity` elemento. Il `dependentOS` e `dependentAssembly` elementi si escludono a vicenda: uno o l'altro deve esistere per un `dependency` elemento, ma non entrambi.  
  
 `dependentAssembly`presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`dependencyType`|Obbligatorio. Specifica il tipo di dipendenza. I valori validi sono `preprequisite` e `install`. Un `install` assembly viene installato come parte di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. A `prerequisite` assembly deve essere presente nella global assembly cache (GAC) prima di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] possibile installare l'applicazione.|  
|`allowDelayedBinding`|Obbligatorio. Specifica se l'assembly può essere caricato a livello di codice in fase di esecuzione.|  
|`group`|Facoltativo. Se il `dependencyType` attributo è impostato su `install`, definisce un gruppo denominato di assembly che vengono installati solo su richiesta. Per altre informazioni, vedere [Procedura dettagliata: Download di assembly su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Se impostato su `framework` e `dependencyType` attributo è impostato su `prerequisite`, definisce l'assembly come parte di .NET Framework. La cache di assembly globale (GAC) non viene controllata per questo assembly durante l'installazione in [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] e versioni successive.|  
|`codeBase`|Obbligatorio quando il `dependencyType` attributo è impostato su `install`. Il percorso dell'assembly dipendente. Può essere un percorso assoluto o un percorso relativo al codice del manifesto di base. Questo percorso deve essere un URI valido affinché il manifesto dell'assembly sia valido.|  
|`size`|Obbligatorio quando il `dependencyType` attributo è impostato su `install`. Le dimensioni dell'assembly dipendente, in byte.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentAssembly` e ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome dell'applicazione.|  
|`version`|Obbligatorio. Specifica il numero di versione dell'applicazione nel formato seguente:`major.minor.build.revision`|  
|`publicKeyToken`|Facoltativo. Specifica una stringa esadecimale a 16 caratteri che rappresenta gli ultimi 8 byte del `SHA-1` hash del valore della chiave pubblica utilizzata per firmare l'assembly. La chiave pubblica utilizzata per firmare il catalogo deve essere maggiore o 2048 bit.|  
|`processorArchitecture`|Facoltativo. Specifica il processore. I valori validi sono `x86` per Windows a 32 bit e `I64` per Windows a 64 bit.|  
|`language`|Facoltativo. Identifica i codici di lingua di due parti, ad esempio EN-US, dell'assembly.|  
  
### <a name="hash"></a>hash  
 Il `hash` elemento è un elemento figlio facoltativo del `assemblyIdentity` elemento. Il `hash` elemento non ha attributi.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]utilizza un hash algoritmico di tutti i file in un'applicazione come un controllo di sicurezza, per verificare che nessuno dei file sono stati modificati dopo la distribuzione. Se il `hash` elemento non viene incluso, questo controllo non verrà eseguito. Pertanto, omettendo il `hash` elemento non è consigliato.  
  
### <a name="dsigtransforms"></a>dsig: Transforms  
 Il `dsig:Transforms` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:Transforms` elemento non ha attributi.  
  
### <a name="dsigtransform"></a>dsig: Transform  
 Il `dsig:Transform` elemento è un elemento figlio obbligatorio del `dsig:Transforms` elemento. Il `dsig:Transform` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per calcolare il digest per questo file. L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 Il `dsig:DigestMethod` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:DigestMethod` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per calcolare il digest per questo file. L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### <a name="dsigdigestvalue"></a>dsig:  
 Il `dsig:DigestValue` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:DigestValue` elemento non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.  
  
## <a name="remarks"></a>Note  
 Tutti gli assembly utilizzati dall'applicazione devono avere un corrispondente `dependency` elemento. Gli assembly dipendenti non includono assembly che devono essere preinstallati nella global assembly cache come assembly di piattaforma.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra `dependency` elementi in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. Questo esempio di codice fa parte di un esempio più esaustivo disponibile per il [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md) argomento.  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<dipendenza > elemento](../deployment/dependency-element-clickonce-deployment.md)