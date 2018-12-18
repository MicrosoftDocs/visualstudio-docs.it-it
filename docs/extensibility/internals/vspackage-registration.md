---
title: Registrazione di VSPackage | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1405fbeba34f3e3aa9c645f6eaffe90fe6ac9036
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-registration"></a>Registrazione di VSPackage
Pacchetti VSPackage devono avvertire [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che vengono installati e che deve essere caricato. Questo processo viene eseguito scrivendo informazioni nel Registro di sistema. Che è un processo tipico di un programma di installazione.  
  
> [!NOTE]
>  È una prassi durante lo sviluppo di VSPackage per usare registrazione automatica. Tuttavia, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partner non può essere rilasciato i loro prodotti tramite registrazione automatica come parte del programma di installazione.  
  
 Le voci del Registro di sistema in un pacchetto Windows Installer vengono in genere stabilite nella tabella del Registro di sistema. È anche possibile registrare le estensioni di file nella tabella del Registro di sistema. Tuttavia, Windows Installer fornisce supporto incorporato mediante l'identificatore programmatico (ProgId), classe, estensione e le tabelle di verbo. Per ulteriori informazioni, vedere [tabelle di Database](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Assicurarsi che le voci del Registro di sistema siano associate al componente che è appropriato per la scelta strategia side-by-side. Ad esempio, le voci del Registro di sistema per un file condiviso devono essere associate con il componente di Windows Installer del file. Analogamente, le voci del Registro di sistema per un file specifico della versione devono essere associate con il componente del file. In caso contrario, installare o disinstallare il pacchetto VSPackage per una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe interrompere il pacchetto VSPackage in altre versioni. Per ulteriori informazioni, vedere [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Il modo più semplice per gestire la registrazione è utilizzare gli stessi dati negli stessi file per la registrazione di sviluppatore e registrazione in fase di installazione. Ad esempio, alcuni strumenti di sviluppo di programma di installazione possono utilizzare file in formato con estensione reg in fase di compilazione. Se gli sviluppatori di gestiscono i file con estensione reg per sviluppo quotidiane e il debug, tali file possono essere inclusi nel programma di installazione automaticamente. Se non è possibile condividere automaticamente i dati di registrazione, è necessario assicurarsi che la copia del programma di installazione dei dati di registrazione sia corrente.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrazione di pacchetti VSPackage non gestiti  
 Pacchetti VSPackage non gestiti (inclusi quelli generati dal modello di Visual Studio pacchetto) utilizzano i file con estensione RGS stile ATL per archiviare le informazioni di registrazione. Il formato del file con estensione RGS è specifico di ATL e non può essere utilizzato in genere come-è per un'installazione dello strumento di creazione. Informazioni di registrazione per il programma di installazione del pacchetto VSPackage devono essere gestite separatamente. Ad esempio, gli sviluppatori possono mantenere i file in formato con estensione reg sincronizzato con RGS modifiche al file. I file con estensione reg possono essere uniti con RegEdit per progetti di sviluppo o utilizzati da un programma di installazione.  
  
## <a name="registering-managed-vspackages"></a>Registrazione di pacchetti VSPackage gestiti  
 Lo strumento RegPkg legge gli attributi di registrazione da un pacchetto VSPackage gestito e sia possibile scrivere le informazioni direttamente al Registro di sistema o al file di formato con estensione reg scrittura che possono essere utilizzati da un programma di installazione.  
  
> [!NOTE]
>  Lo strumento RegPkg non è ridistribuibile e non può essere utilizzato per registrare un VSPackage nel sistema dell'utente.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Perché i pacchetti VSPackage devono non effettuare la registrazione automatica in fase di installazione  
 I programmi di installazione del pacchetto VSPackage deve fare affidamento su registrazione automatica. A prima vista, mantenendo i valori del Registro di sistema di un VSPackage solo nel pacchetto VSPackage stesso dovrebbe essere una buona idea. Dato che gli sviluppatori sono necessari i valori del Registro di sistema disponibili per le operazioni di routine e test, è opportuno evitare di mantenere una copia separata dei dati del Registro di sistema nel programma di installazione. Il programma di installazione può basarsi su VSPackage per scrivere i valori del Registro di sistema.  
  
 Buona in teoria, durante la registrazione automatica presenta diversi difetti che rendono non appropriati per l'installazione di VSPackage:  
  
-   Supporto di installazione, disinstallazione, il rollback dell'installazione e disinstallazione rollback correttamente è necessario creare quattro azioni personalizzate per ogni pacchetto VSPackage gestito che esegue la registrazione automatica chiamando RegPkg.  
  
-   L'approccio adottato per supporto side-by-side potrebbe richiedere che si creano quattro azioni personalizzate che richiamano RegSvr32 o RegPkg per ogni versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Un'installazione con i moduli di registrazione automatica non è possibile rollback in modo sicuro in quanto non è possibile indicare se le chiavi di registrazione automatica vengono utilizzate da un'altra applicazione o funzionalità.  
  
-   DLL di registrazione automatica collegare talvolta per ausiliarie DLL che non sono presenti o sono una versione errata. Al contrario, Windows Installer è possibile registrare le DLL utilizzando le tabelle del Registro di sistema senza dipendenza lo stato corrente del sistema.  
  
-   Codice di registrazione automatica può essere negato l'accesso alle risorse di rete, ad esempio librerie dei tipi, se un componente sia specificato come esecuzione dall'origine e viene elencato nella tabella SelfReg. Ciò può causare l'installazione del componente esito negativo durante un'installazione amministrativa.  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Registrazione del pacchetto gestito](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)