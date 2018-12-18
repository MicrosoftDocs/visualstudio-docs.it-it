---
title: '&lt;assembly&gt; elemento (applicazione ClickOnce) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31ac0f127dea4d668afe66c064b5e871d927f04e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;assembly&gt; elemento (applicazione ClickOnce)
L'elemento di primo livello per il manifesto dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `assembly` elemento è l'elemento radice ed è obbligatorio. Il primo elemento di contenuto deve essere un `assemblyIdentity` elemento. Gli elementi del manifesto devono essere in uno degli spazi dei nomi seguenti:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Gli elementi figlio dell'assembly devono essere anche in questi spazi dei nomi, per ereditarietà o per l'assegnazione di tag.  
  
 Il `assembly` elemento presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`manifestVersion`|Obbligatorio. Il `manifestVersion` attributo deve essere impostato su `1.0`.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato un `assembly` elemento in un manifesto dell'applicazione per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assembly > elemento](../deployment/assembly-element-clickonce-deployment.md)