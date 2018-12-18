---
title: '&lt;assembly&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
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
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ab58cb90f9486c3a233d5173db340be3ee5f034
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;assembly&gt; elemento (distribuzione di ClickOnce)
L'elemento di primo livello per il manifesto di distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `assembly` elemento è l'elemento radice ed è obbligatorio. Il primo elemento di contenuto deve essere un `assemblyIdentity` elemento. Gli elementi del manifesto devono essere in spazi dei nomi seguenti: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, e `http://www.w3.org/2000/09/xmldsig#`. Gli elementi figlio dell'assembly devono essere anche in questi spazi dei nomi, per ereditarietà o per l'assegnazione di tag.  
  
 Il `assembly` elemento presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`manifestVersion`|Obbligatorio. Questo attributo deve essere impostato su `1.0`.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato un `assembly` elemento in un manifesto di distribuzione per un'applicazione distribuita mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile per il [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) argomento.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly > elemento](../deployment/assembly-element-clickonce-application.md)