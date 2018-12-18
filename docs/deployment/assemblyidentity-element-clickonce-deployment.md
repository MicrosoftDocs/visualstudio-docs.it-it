---
title: '&lt;assemblyIdentity&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 802d94063d2a4351ecc627c9426edb458d2543c2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; elemento (distribuzione di ClickOnce)
Identifica l'assembly primario del [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `assemblyIdentity` elemento è obbligatorio. Non contiene elementi figlio e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome leggibile dall'utente della distribuzione per scopi informativi.<br /><br /> Se `name` contiene caratteri speciali, ad esempio le virgolette singole o doppie, potrebbe essere Impossibile attivare l'applicazione.|  
|`version`|Obbligatorio. Specifica il numero di versione dell'assembly, nel formato seguente: `major.minor.build.revision`.<br /><br /> Questo valore deve essere incrementato in un manifesto aggiornato per attivare un aggiornamento dell'applicazione.|  
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale a 16 caratteri che rappresenta il valore hash SHA-1 della chiave pubblica utilizzata per firmare il manifesto di distribuzione agli ultimi 8 byte. La chiave pubblica che viene utilizzata per firmare deve essere 2048 bit o superiore.<br /><br /> Anche se la firma di un assembly è facoltativo ma consigliato, questo attributo è obbligatorio. Se un assembly è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore "fittizio" di tutti gli zeri.|  
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono `msil` per tutti i processori, `x86` per Windows a 32 bit, `IA64` per Windows a 64 bit, e `Itanium` per processori Intel a 64 bit Itanium.|  
|`type`|Obbligatorio. Per garantire la compatibilità con la tecnologia Windows installazione side-by-side. L'unico valore consentito è `win32`.|  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato un `assemblyIdentity` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione. Questo esempio di codice fa parte di un esempio più esaustivo disponibile per il [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) argomento.  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-application.md)