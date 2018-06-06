---
title: '&lt;postAction&gt; elemento (sviluppo per Office in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dcab31eea406da695bdedd21b21c0d86cacea220
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693117"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `postAction` dello spazio dei nomi `vstav3` contiene gli elementi `entrypoint` e tutti gli elementi `postActionData` associati alle azioni post-distribuzione, che vengono eseguite dopo l'installazione delle soluzioni Office.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `postAction` è facoltativo e si trova nello spazio dei nomi `vstav3` . Per ogni azione post-distribuzione è definito un elemento `postAction` in un manifesto dell'applicazione.  
  
 L'elemento `postAction` non ha attributi.  
  
 `postAction` presenta gli elementi seguenti:  
  
### <a name="entrypoint"></a>entrypoint  
 Facoltativo. Il ruolo del `entryPoint` elemento il `vstav3` dello spazio dei nomi è definito in [ &#60;entryPoints&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### <a name="postactiondata"></a>postActionData  
 Facoltativo. Il ruolo del `postActionData` elemento il `vstav3` dello spazio dei nomi è definito in [ &#60;postActionData&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Esempio di azione post-distribuzione  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra l'elemento `postAction` in un manifesto dell'applicazione per una soluzione Office distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```xml
<vstav3:postAction>  
  <vstav3:entryPoint   
    class="PostDeploymentAction.PostDeploymentActionSample">  
    <assemblyIdentity   
      name="PostDeploymentAction"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:postActionData>  
  </vstav3:postActionData>  
</vstav3:postAction>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto dell'applicazione ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  