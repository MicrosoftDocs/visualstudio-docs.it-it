---
title: '&lt;dipendenza&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
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
helpviewer_keywords: <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: "27"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 8716da20c989a1a8d1e36d9e071e9802a06219bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;dipendenza&gt; elemento (distribuzione di ClickOnce)
Identifica la versione dell'applicazione da installare e il percorso del manifesto dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `dependency` elemento è obbligatorio. Non dispone di attributi. Un manifesto di distribuzione può avere più `dependency` elementi.  
  
 Il `dependency` elemento descrive in genere le dipendenze dell'applicazione principale dagli assembly contenuti in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Se l'applicazione Main.exe utilizza un assembly denominato DotNetAssembly. dll, tale assembly deve essere elencato in una sezione di dipendenza. Dipendenza, tuttavia, può inoltre essere formulata altri tipi di dipendenze, ad esempio le dipendenze da una versione specifica di common language runtime, in un assembly nella global assembly cache (GAC) o su un oggetto COM. Perché è una tecnologia di distribuzione no-touch, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non è possibile avviare il download e installazione di questi tipi di dipendenze, ma ne impedisce l'esecuzione dell'applicazione se uno o più dipendenze specificate non esistono.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Obbligatorio. Questo elemento contiene il `assemblyIdentity` elemento. Nella tabella seguente vengono illustrati gli attributi di `dependentAssembly` supporta.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`preRequisite`|Facoltativo. Specifica che l'assembly deve essere già esistente nella GAC. I valori validi sono `true` e `false`. Se `true`e l'assembly specificato non esiste nella GAC, l'applicazione non viene eseguito correttamente.|  
|`visible`|Facoltativo. Identifica l'identità di applicazione di livello superiore, incluse le relative dipendenze. Utilizzato internamente da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per gestire l'archiviazione di applicazioni e attivazione.|  
|`dependencyType`|Obbligatorio. La relazione tra questa dipendenza e l'applicazione. I valori validi sono:<br /><br /> -   `install`. Componente rappresenta un'installazione distinta dall'applicazione corrente.<br />-   `preRequisite`. Componente è necessario per l'applicazione corrente.|  
|`codebase`|Facoltativo. Il percorso completo del manifesto dell'applicazione.|  
|`size`|Facoltativo. Le dimensioni del manifesto dell'applicazione, in byte.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentAssembly`. Il contenuto di `assemblyIdentity` deve essere identico a quello descritto nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. Nella tabella seguente vengono illustrati gli attributi del `assemblyIdentity` elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Identifica il nome dell'applicazione.|  
|`Version`|Obbligatorio. Specifica il numero di versione dell'applicazione, nel formato seguente:`major.minor.build.revision`|  
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale a 16 caratteri che rappresenta gli ultimi 8 byte dell'hash SHA-1 della chiave pubblica utilizzata per firmare l'assembly. La chiave pubblica utilizzata per firmare deve essere 2048 bit o superiore.|  
|`processorArchitecture`|Obbligatorio. Specifica il microprocessore. I valori validi sono `x86` per Windows a 32 bit e `IA64` per Windows a 64 bit.|  
|`Language`|Facoltativo. Identifica i codici di lingua di due parti dell'assembly. Ad esempio EN-US, che è l'acronimo per inglese (Stati Uniti). Il valore predefinito è `neutral`. Questo elemento è presente il `asmv2` dello spazio dei nomi.|  
|`type`|Facoltativo. Per le versioni precedenti della tecnologia di installazione la compatibilità con Windows side-by-side. L'unico valore consentito è `win32`.|  
  
## <a name="hash"></a>hash  
 Il `hash` elemento è un elemento figlio facoltativo del `file` elemento. Il `hash` elemento non ha attributi.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]utilizza un hash algoritmico di tutti i file in un'applicazione come un controllo di sicurezza per verificare che nessuno dei file sono stati modificati dopo la distribuzione. Se il `hash` elemento non viene incluso, questo controllo non verrà eseguito. Pertanto, omettendo il `hash` elemento non è consigliato.  
  
## <a name="dsigtransforms"></a>dsig: Transforms  
 Il `dsig:Transforms` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:Transforms` elemento non ha attributi.  
  
## <a name="dsigtransform"></a>dsig: Transform  
 Il `dsig:Transform` elemento è un elemento figlio obbligatorio del `dsig:Transforms` elemento. Nella tabella seguente vengono illustrati gli attributi del `dsig:Transform` elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per calcolare il digest per questo file. L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 Il `dsig:DigestMethod` elemento è un elemento figlio obbligatorio del `hash` elemento. Nella tabella seguente vengono illustrati gli attributi del `dsig:DigestMethod` elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per calcolare il digest per questo file. L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig:  
 Il `dsig:DigestValue` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:DigestValue` elemento non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.  
  
## <a name="remarks"></a>Note  
 Manifesti di distribuzione dispongono in genere un singolo `assemblyIdentity` elemento che identifica il nome e la versione del manifesto dell'applicazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un `dependency` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente specifica una dipendenza su un assembly già installato nella Global Assembly Cache.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente specifica una dipendenza da una versione specifica di common language runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente specifica una dipendenza del sistema operativo.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md)