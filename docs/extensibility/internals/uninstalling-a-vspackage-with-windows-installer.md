---
title: La disinstallazione di un pacchetto VSPackage con Windows Installer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee8ad89e02dfa8aebbb39a9d7ebe523ad01bb7e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>La disinstallazione di un pacchetto VSPackage con Windows Installer
La maggior parte, Windows Installer possibile disinstallare il pacchetto VSPackage solo da "annullamento" eseguite per installare il pacchetto VSPackage. Le azioni personalizzate illustrate [comandi che devono essere eseguiti dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md) deve essere eseguito dopo una disinstallazione anche. Poiché le chiamate a devenv.exe si verificano subito prima dell'azione InstallFinalize standard per l'installazione e la disinstallazione, le voci della tabella CustomAction e InstallExecuteSequence soddisfare entrambi i casi.  
  
> [!NOTE]
>  Eseguire `devenv /setup` dopo la disinstallazione di un pacchetto MSI.  
  
 Come regola generale, se si aggiungono le azioni personalizzate a un pacchetto Windows Installer, è necessario gestire tali azioni durante la disinstallazione e rollback. Se si aggiungono le azioni personalizzate per il pacchetto VSPackage effettuare la registrazione automatica, ad esempio, è necessario aggiungere azioni personalizzate per annullare la registrazione, troppo.  
  
> [!NOTE]
>  È possibile che un utente di installare il pacchetto VSPackage e quindi disinstallare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con cui è integrato. È possibile garantire che la disinstallazione del VSPackage funziona in tale scenario tramite l'eliminazione di azioni personalizzate che eseguono il codice con dipendenze su [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Le condizioni di avvio di gestione in fase di disinstallazione.  
 L'azione standard LaunchConditions legge le righe della tabella per mostrare errore LaunchCondition messaggi se non vengono soddisfatte le condizioni. Le condizioni di avvio sono in genere utilizzato per garantire che siano soddisfatti i requisiti di sistema, in genere, è possibile ignorare le condizioni di avvio durante la disinstallazione aggiungendo la condizione, `NOT Installed`, alla riga della tabella LaunchCondition LaunchConditions.  
  
 In alternativa è possibile aggiungere `OR Installed` per avviare le condizioni che non sono importanti durante la disinstallazione. Questo garantisce che la condizione sarà sempre true durante la disinstallazione e pertanto non verrà visualizzato il messaggio di errore di condizione di avvio.  
  
> [!NOTE]
>  `Installed`la proprietà di che Windows Installer imposta quando viene rilevato che il pacchetto VSPackage è stato installato nel sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)