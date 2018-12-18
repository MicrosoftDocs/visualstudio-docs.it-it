---
title: Opzioni della riga di comando devenv per lo sviluppo di VSPackage | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 18c531bb849793de184f3797067dceff4bd10199
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]consente agli sviluppatori di automatizzare le attività dalla riga di comando quando si esegue devenv.exe, del file che avvia l'ambiente di sviluppo integrato (IDE) di Visual Studio.  
  
 Le attività includono:  
  
-   Distribuzione di applicazioni in configurazioni predefinite da all'esterno dell'IDE.  
  
-   Automaticamente tramite i set di impostazioni di compilazione di progetti le impostazioni di compilazione o configurazioni di debug.  
  
-   Durante il caricamento dell'IDE in configurazioni specifiche, tutto da all'esterno dell'IDE. Inoltre, è possibile personalizzare l'IDE all'avvio.  
  
## <a name="guidelines-for-switches"></a>Linee guida per i commutatori  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]documentazione vengono descritte le opzioni della riga di comando devenv a livello di utente. Per ulteriori informazioni, vedere [opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md). Devenv supporta anche altre opzioni della riga di comando che sono utili con VSPackage sviluppo, distribuzione e debug.  
  
|Opzione della riga di comando|Descrizione|  
|--------------------------|-----------------|  
|/SafeMode|Avvia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria, caricando solo l'IDE predefinito e i servizi. Il commutatore /safemode impedisce a tutti i pacchetti VSPackage di terze parti di caricare quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene avviato, garantendo quindi un'esecuzione stabile.<br /><br /> Questa opzione non accetta argomenti.|  
|/resetskippkgs|Cancella tutti ignorare le opzioni di caricamento che sono stati aggiunti dagli utenti che vogliono evitare il caricamento di pacchetti VSPackage problematici, quindi avvia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. Cancellare il tag riabilita il caricamento del pacchetto VSPackage.<br /><br /> Questa opzione non accetta argomenti.|  
|/rootsuffix|Avvia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzando un percorso alternativo. Il seguente comando viene eseguito il collegamento creato dal [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] programma di installazione:<br /><br /> devenv /RootSuffix exp<br /><br /> In questo caso, exp identifica una posizione con un suffisso specifico, ad esempio 10.0Exp anziché 10.0. L'istanza sperimentale consente di eseguire il debug di un pacchetto VSPackage separatamente dall'istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che si utilizza per scrivere codice.<br /><br /> Questa opzione può accettare qualsiasi stringa che identifica un percorso a cui è stato creato tramite VSRegEx.exe. Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).|  
|/Splash|Viene illustrato il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] schermata come di consueto e quindi visualizza una finestra di messaggio prima della visualizzazione IDE principale. La finestra di messaggio consente di esaminare la schermata iniziale, per cercare un'icona di prodotto VSPackage, ad esempio.<br /><br /> Questa opzione non accetta argomenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta della riga di comando](../extensibility/adding-command-line-switches.md)   
 [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)