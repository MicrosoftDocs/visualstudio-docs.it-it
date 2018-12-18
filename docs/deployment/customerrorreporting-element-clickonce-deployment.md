---
title: '&lt;customErrorReporting&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41ade854a37127443735e1c197c080aad3d5bd93
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
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