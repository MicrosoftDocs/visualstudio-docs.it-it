---
title: 'Procedura: specificare i file di Log dettagliati per le distribuzioni ClickOnce | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8153625ec875cb54b0fc7b626d0cef61df2e9b71
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedura: specificare i file di log dettagliati per le distribuzioni ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gestisce i file di log attività per tutte le distribuzioni. Questi registri documentare i dettagli relativi a installazione, l'inizializzazione, aggiornamento e disinstallazione di un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per aumentare il livello di dettaglio che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scritture nei file di log, utilizzare l'Editor del Registro di sistema (**regedit.exe**) per specificare il livello di dettaglio.  
  
> [!CAUTION]
>  Se si utilizza l'Editor del Registro di sistema in modo non corretto, si può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.  
  
 La procedura seguente viene descritto come specificare il livello di dettaglio per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di log per l'utente corrente. Per ridurre il livello di dettaglio, rimuovere il valore del Registro di sistema.  
  
### <a name="to-specify-verbose-log-files"></a>Per specificare i file di log dettagliati  
  
1.  Aprire **Regedit.exe**.  
  
2.  Passare al nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Se necessario, creare un nuovo valore stringa denominato `LogVerbosityLevel`.  
  
4.  Impostare il `LogVerbosityLevel` valore `1`.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)