---
title: Scelta tra package VS condivisi e con controllo delle versioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce7f58d664c6a186146272af16324be2fee90983
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Scelta tra package VS condivisi e con controllo delle versioni
Versioni diverse di Visual Studio possono coesistere nello stesso computer. Pacchetti VSPackage possono supportare qualsiasi combinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versioni.  
  
 È possibile abilitare le installazioni side-by-side di VSPackage tramite una delle due strategie, la strategia condivisa o la strategia di controllo delle versioni. Entrambi contenere la presenza di più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e associate le versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 La strategia condiviso, un VSPackage è registrato per l'uso in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La strategia con controllo delle versioni, sono installate più DLL VSPackage, uno per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportate.  
  
## <a name="shared-vspackages"></a>Package VS condivisi  
 Utilizzando un package VS condivisi è appropriato quando si utilizza lo stesso VSPackage in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per implementare un package VS condivisi, è necessario eseguire i passaggi seguenti:  
  
-   Rendere il pacchetto VSPackage compatibili con più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Due modalità di esecuzione sono pertanto disponibili:  
  
    -   Limitare il pacchetto VSPackage per utilizzando solo le funzionalità della versione meno recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportate.  
  
    -   Il pacchetto VSPackage per adattarsi alla versione del programma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in cui è in esecuzione. Quindi, se le query per i servizi più recenti hanno esito negativo, il pacchetto VSPackage può offrire altri servizi che sono supportati nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registrare il VSPackage in modo appropriato. Per ulteriori informazioni, vedere [registrazione VSPackage](../extensibility/internals/vspackage-registration.md) e [registrazione del pacchetto VSPackage gestito](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrare le estensioni di file in modo appropriato. Per ulteriori informazioni, vedere [la registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Creare un programma di installazione che consente di distribuire il pacchetto VSPackage per le versioni appropriate di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [l'installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gestione dei componenti](../extensibility/internals/component-management.md).  
  
-   Per risolvere il problema dei conflitti di registrazione. Per ulteriori informazioni, vedere [registrazione VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Verificare che i file condivisi sia con controllo delle versioni rispettino per consentire l'installazione sicura e la rimozione di più versioni di conteggio dei riferimenti. Per ulteriori informazioni, vedere [gestione dei componenti](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Versione VSPackage  
 Sotto la strategia di VSPackage con controllo delle versioni, si crea un pacchetto VSPackage per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportate. In questo modo è appropriato quando si prevede di sfruttare i vantaggi dei servizi forniti da versioni più recenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], perché ogni VSPackage può evolvere senza influire sulle altre. Tuttavia, la strategia di controllo delle versioni di creazione di più file binari, da una sola codebase o da più basi di codice indipendente, può implicare più attività iniziali di sviluppo più la strategia condivisa. Inoltre, operazioni di configurazione aggiuntive potrebbero essere necessarie poiché è necessario creare un programma di installazione separato per ogni versione o un singolo programma di installazione che consente di rilevare le versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che siano installati e che supporta il pacchetto VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilità binaria  
 In genere, la compatibilità binaria consente a codice nativo VSPackage sviluppati con versioni precedenti di Visual Studio da eseguire in versioni successive di Visual Studio. Tuttavia, esistono tre importanti eccezioni:  
  
-   Se il pacchetto VSPackage si basa su una particolare versione di common language runtime, è necessario determinare in quale versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è in esecuzione.  
  
-   Un pacchetto VSPackage potrebbe essere una dipendenza su una funzionalità specifica di un altro VSPackage o un altro prodotto. Di conseguenza, il pacchetto VSPackage può essere eseguito solo in cui la dipendenza viene soddisfatta.  
  
-   Un pacchetto VSPackage può essere influenzato da una correzione di sicurezza in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack o una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In questi casi, un pacchetto VSPackage sviluppate con una versione precedente del [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] potrebbe non essere eseguito nelle versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dopo la correzione di sicurezza è stata applicata. Tuttavia, è possibile ricompilare il pacchetto con la versione più recente e anche eseguirlo nelle versioni precedenti.  
  
 VSPackage gestiti devono essere compilati utilizzando una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] che corrisponde alla versione di destinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Oltre alla pianificazione per la compatibilità binaria per i file binari di VSPackage, inoltre deve considerare soluzioni e formati di file di progetto. Se il pacchetto VSPackage crea un nuovo tipo di progetto, è necessario decidere se è possibile eseguire solo una versione o in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [l'aggiornamento dei progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Vedere anche  
 [L'installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestione dei componenti](../extensibility/internals/component-management.md)