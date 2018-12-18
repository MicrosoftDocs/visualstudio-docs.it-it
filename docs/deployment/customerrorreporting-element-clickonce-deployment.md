---
title: '&lt;customErrorReporting&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b6b6726ebf45522834d916897f456952b66a3605
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; elemento (distribuzione di ClickOnce)
Specifica un URI da visualizzare quando si verifica un errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Note  
 Questo elemento è facoltativo. Senza di esso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visualizza una finestra di dialogo di errore con lo stack dell'eccezione. Se il `customErrorReporting` elemento è presente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà invece visualizzato l'URI indicato dal `uri` parametro. L'URI di destinazione include la classe di eccezione esterna, la classe di eccezione interna e il messaggio di eccezione interna come parametri.  
  
 Utilizzare questo elemento per aggiungere funzionalità di segnalazione per l'applicazione. Poiché l'URI generato include informazioni sul tipo di errore, il sito Web è possibile analizzare tali informazioni e visualizzare, ad esempio, una schermata di risoluzione dei problemi appropriata.  
  
## <a name="example"></a>Esempio  
 Il frammento di codice seguente viene illustrato il `customErrorReporting` elemento, con l'URI generato che potrebbe produrre.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)