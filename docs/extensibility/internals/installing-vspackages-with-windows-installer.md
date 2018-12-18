---
title: L'installazione di pacchetti VSPackage con Windows Installer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a9f4d45c3fccebed9febc2ea722981f597896ace
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="installing-vspackages-with-windows-installer"></a>L'installazione di pacchetti VSPackage con Windows Installer
L'integrazione di VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede più di un semplice copia i file nel computer dell'utente. Programma di installazione del VSPackage è necessario installare il pacchetto VSPackage e i relativi file dipendenti e registrare e integrarli in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il pacchetto VSPackage può sfruttare le funzionalità di integrazione, ad esempio la visualizzazione di un'icona nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iniziale dello schermo e la finestra di dialogo informazioni su.  
  
 File di Microsoft Windows Installer sono il modo consigliato per distribuire i VSPackage. Eseguire i pacchetti di Windows Installer da utilizzare in qualsiasi sistema operativo Windows supportato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Viene fornita una panoramica di Windows Installer.  
  
 [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Vengono illustrati modi diversi, è possibile supportare le installazioni side-by-side di entrambi i VSPackage e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Creazione e modifica di un pacchetto di Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Viene fornita una panoramica dei passaggi tipici seguire i programmi di installazione per installare correttamente e integrare VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Viene descritto come è possibile individuare un programma di installazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e i componenti e Annulla l'installazione se non vengono soddisfatti i requisiti di VSPackage.  
  
 [Gestione dei componenti](../../extensibility/internals/component-management.md)  
 Descrive come sviluppare un programma di installazione che manterrà l'integrità delle versioni precedenti del prodotto.  
  
 [Scelta della directory di installazione per un pacchetto VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Vengono riepilogate le opzioni per l'individuazione di VSPackage.  
  
 [Registrazione di pacchetti VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Viene illustrato come vengono registrati i pacchetti VSPackage in fase di installazione e perché registrazione automatica è una buona idea.  
  
 [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)  
 Viene descritto come usare al nuovo Sil aggregator tipo di progetto per i tipi di progetto di codice gestito.  
  
 [Procedura: Generare le informazioni del Registro di sistema per un programma di installazione](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Viene illustrato come utilizzare RegPkg.exe per generare un manifesto di registrazione per un pacchetto VSPackage gestito.  
  
 [Comandi da eseguire dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Viene illustrato come eseguire i comandi di post-installazione per l'integrazione di VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Disinstallazione di un pacchetto VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Descrive i passaggi che del programma di installazione è necessario eseguire quando gli utenti disinstallano il pacchetto VSPackage.  