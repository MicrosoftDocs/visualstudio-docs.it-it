---
title: '&lt;assemblyIdentity&gt; elemento (applicazione ClickOnce) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: "20"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b731522897512300459a32f8e01c4d54277eaa5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt; elemento (applicazione ClickOnce)
Identifica l'applicazione distribuita in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `assemblyIdentity` elemento è obbligatorio. Non contiene elementi figlio e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Identifica il nome dell'applicazione.<br /><br /> Se `Name` contiene caratteri speciali, ad esempio le virgolette singole o doppie, potrebbe essere Impossibile attivare l'applicazione.|  
|`Version`|Obbligatorio. Specifica il numero di versione dell'applicazione nel formato seguente:`major.minor.build.revision`|  
|`publicKeyToken`|Facoltativo. Specifica una stringa esadecimale a 16 caratteri che rappresenta gli ultimi 8 byte del `SHA-1` hash del valore della chiave pubblica utilizzata per firmare l'assembly. La chiave pubblica utilizzato per firmare il catalogo deve essere 2048 bit o superiore.<br /><br /> Anche se la firma di un assembly è facoltativo ma consigliato, questo attributo è obbligatorio. Se un assembly è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore "fittizio" di tutti gli zeri.|  
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono `msil` per tutti i processori, `x86` per Windows a 32 bit, `IA64` per Windows a 64 bit, e `Itanium` per processori Intel a 64 bit Itanium.|  
|`language`|Obbligatorio. Identifica i codici di lingua di due parti (ad esempio, `en-US`) dell'assembly. Questo elemento è presente il `asmv2` dello spazio dei nomi. Se non viene specificato, il valore predefinito è `neutral`.|  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Descrizione  
 Nell'esempio di codice seguente viene illustrato un `assemblyIdentity` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Codice  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)