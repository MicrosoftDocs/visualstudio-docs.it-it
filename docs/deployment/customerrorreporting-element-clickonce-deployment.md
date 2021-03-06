---
title: '&lt;&gt;elemento customErrorReporting (distribuzione ClickOnce) | Microsoft Docs'
description: L'elemento customErrorReporting specifica un URI da visualizzare quando si verifica un errore anziché una finestra di dialogo di errore che mostra lo stack dell'eccezione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b168b3bcb90ae758609698de306928eb7e13d909
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888485"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;elemento customErrorReporting (distribuzione ClickOnce)
Specifica un URI da visualizzare quando si verifica un errore.

## <a name="syntax"></a>Sintassi

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Osservazioni
 Questo elemento è facoltativo. Senza di esso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visualizza una finestra di dialogo di errore che mostra lo stack dell'eccezione. Se l' `customErrorReporting` elemento è presente, visualizzerà [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] invece l'URI indicato dal `uri` parametro. L'URI di destinazione includerà la classe di eccezione esterna, la classe di eccezione interna e il messaggio di eccezione interna come parametri.

 Utilizzare questo elemento per aggiungere la funzionalità di segnalazione errori all'applicazione. Poiché l'URI generato include informazioni sul tipo di errore, il sito Web può analizzare tali informazioni e visualizzare, ad esempio, una schermata appropriata per la risoluzione dei problemi.

## <a name="example"></a>Esempio
 Il frammento di codice seguente mostra l' `customErrorReporting` elemento, insieme all'URI generato che può produrre.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Vedi anche
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)