---
title: Riferimenti alle API non gestite ClickOnce | Documenti Microsoft
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
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: cplusplus
ms.openlocfilehash: 392ada2288adcc229834f617c2f6284bb2e7ed0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>Riferimenti alle API non gestite ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]API pubbliche non gestite da dfshim.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Pulisce o disinstalla tutte le applicazioni in linea dal [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache dell'applicazione.  
  
### <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Note  
 La chiamata a CleanOnlineAppCache avvia il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] del servizio se non è già in esecuzione.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Recupera le informazioni di distribuzione dall'URL manifesto e l'attivazione.  
  
### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|Tipo|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Un puntatore al `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Un puntatore al `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Un puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica l'identità dell'applicazione completo restituito.|LPWSTR|  
|`pdwIdentityBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzApplicationIdentity` buffer, in WCHAR. Include lo spazio per il carattere di terminazione NULL.|LPDWORD|  
|`pwzProcessorArchitecture`|Puntatore a un buffer per la ricezione di una stringa con terminazione NULL che specifica l'architettura del processore della distribuzione dell'applicazione, nel manifesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzProcessorArchitecture` buffer, in WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Puntatore a un buffer per la ricezione di una stringa con terminazione NULL che specifica la codebase del manifesto dell'applicazione, nel manifesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzApplicationManifestCodebase` buffer, in WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Un puntatore a un buffer per la ricezione di una stringa con terminazione NULL che specifica il provider di distribuzione dal manifesto, se presente. In caso contrario, viene restituita una stringa vuota.|LPWSTR|  
|`pdwProviderBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un HRESULT che rappresenta l'errore. Restituisce HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) se un buffer è troppo piccolo.  
  
### <a name="remarks"></a>Note  
 I puntatori non devono essere null. `pcwzActivationUrl`e `pcwzPathToDeploymentManifest` non deve essere vuoto.  
  
 È responsabilità del chiamante per pulire l'URL di attivazione. Ad esempio, aggiungendo caratteri di escape in cui sono necessari o rimuovendo la stringa di query.  
  
 È responsabilità del chiamante per limitare la lunghezza di input. Ad esempio, la lunghezza massima dell'URL è 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Avvia o installa un'applicazione utilizzando un URL di distribuzione.  
  
### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|Tipo|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Puntatore a una stringa con terminazione NULL che contiene l'URL del manifesto di distribuzione.|LPCWSTR|  
|`data`|Riservato per utilizzi futuri. Deve essere NULL.|LPVOID|  
|`flags`|Riservato per utilizzi futuri. Deve essere 0.|DWORD|  
  
### <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>