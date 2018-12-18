---
title: '&lt;customHostSpecified&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d74dac27e4d4a5735dc73ebb069d985d17022d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elemento (sviluppo per Office in Visual Studio)
  Il `customHostSpecified` elemento indica che questa soluzione non è un'applicazione autonoma. Soluzioni Office contengono componenti che sono ospitati all'interno di applicazioni di Microsoft Office.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `customHostSpecified` elemento è obbligatorio per le soluzioni Office. Questo elemento è presente il `co.v1` dello spazio dei nomi e specifica che la distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.  
  
 Questo è un elemento figlio del primo `<entrypoint>` elemento nel manifesto dell'applicazione. Non può esistere alcun altri elementi figlio che `<entrypoint>` elemento o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] genererà un errore di convalida durante l'installazione.  
  
 Questo elemento dispone di alcun attributo e non gli elementi figlio.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato il `customHostSpecified` elemento in un manifesto dell'applicazione per una soluzione Office. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  