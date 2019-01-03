---
title: Installazione di pacchetti VSPackage con Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0efb1b5c45595383f62d08399906cbb1b546479
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827835"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installazione di pacchetti VSPackage con Windows Installer
L'integrazione di VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede oltre la semplice copia dei file di computer dell'utente. Programma di installazione del pacchetto VSPackage deve installare il pacchetto VSPackage e i relativi file dipendenti e registrare e integrarle in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il pacchetto VSPackage può sfruttare i vantaggi delle funzionalità di integrazione ad esempio visualizzando un'icona sul [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iniziale dello schermo e sulla finestra di dialogo.  
  
 File di Microsoft Windows Installer sono il modo consigliato per distribuire i pacchetti VSPackage. Eseguire pacchetti di Windows Installer facile da usare in qualsiasi sistema operativo Windows supportato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Fornisce una panoramica del programma di installazione di Windows.  
  
 [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Illustra diversi modi in cui è possibile supportare le installazioni side-by-side di entrambi i VSPackage e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Creazione e modifica di un pacchetto di Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Viene fornita una panoramica dei passaggi tipici seguire i programmi di installazione per installare correttamente e integrare i pacchetti VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Viene descritto come è possibile rilevare un programma di installazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e i suoi componenti e Annulla installazione se il pacchetto VSPackage non sono soddisfatte.  
  
 [Gestione dei componenti](../../extensibility/internals/component-management.md)  
 Viene illustrato come sviluppare un programma di installazione che manterrà l'integrità di versioni precedenti del prodotto.  
  
 [Scelta della directory di installazione per un pacchetto VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Vengono riepilogate le opzioni per l'individuazione di pacchetti VSPackage.  
  
 [Registrazione di pacchetti VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Illustra come i pacchetti VSPackage registrati al momento dell'installazione e perché registrazione automatica è una buona idea.  
  
 [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)  
 Viene illustrato come utilizzare al nuovo Sil aggregator tipo di progetto per i tipi di progetto di codice gestito.  
  
 [Procedura: Genera informazioni di registro di sistema per un programma di installazione](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Viene illustrato come usare RegPkg.exe per generare un manifesto di registrazione per un pacchetto VSPackage gestito.  
  
 [Comandi da eseguire dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Viene illustrato come eseguire i comandi di post-installazione per integrare i pacchetti VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Disinstallazione di un pacchetto VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Descrive la procedura che deve eseguire il programma di installazione quando gli utenti disinstallano il pacchetto VSPackage.  