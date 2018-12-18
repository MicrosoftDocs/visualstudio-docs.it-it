---
title: La gestione delle associazioni di File Side-by-Side | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d0a6f8ec88a49b785b771aef51dc25b5646ffda
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="managing-side-by-side-file-associations"></a>La gestione delle associazioni di File Side-by-Side
Se il pacchetto VSPackage fornisce associazioni di file, è necessario decidere come gestire le installazioni side-by-side in cui una particolare versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere richiamato per aprire un file. Formati di file compatibile composta il problema.  
  
 Gli utenti si aspettano una nuova versione di un prodotto per essere compatibile con le versioni precedenti, in modo che i file esistenti possono essere caricati in una nuova versione senza perdita di dati. In teoria, il pacchetto VSPackage sia caricare e salvare i formati di file con le versioni precedenti. Se non è true, è necessario offrire aggiornare il formato di file per la nuova versione di un VSPackage. Lo svantaggio di questo approccio è che il file aggiornato non può essere aperto in una versione precedente.  
  
 Per evitare questo problema, è possibile modificare le estensioni quando i formati di file è diventato incompatibili. Ad esempio, è possibile utilizzare la versione 1 di un VSPackage l'estensione, .mypkg10 e la versione 2 è possibile utilizzare l'estensione, .mypkg20. Questa differenza identifica il pacchetto VSPackage che apre un file specifico. Se si aggiunge un VSPackage più recente per l'elenco dei programmi che sono associati a un'estensione precedente, gli utenti possono fare doppio clic su file e scegliere di aprirlo in un VSPackage più recente. A questo punto, il pacchetto VSPackage può offrire aggiornare il file al nuovo formato o aprire il file e mantenere la compatibilità con le versioni precedenti del pacchetto VSPackage.  
  
> [!NOTE]
>  È possibile combinare questi approcci. Ad esempio, è possibile offrire compatibilità con le versioni precedenti caricando un file precedenti e consentono di aggiornare il formato di file quando l'utente Salva.  
  
## <a name="facing-the-problem"></a>Il problema riscontrato  
 Se si desidera più side-by-side VSPackage per usare la stessa estensione, è necessario scegliere la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] associato con l'estensione. Di seguito sono disponibili due alternative:  
  
-   Aprire il file nella versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installato nel computer dell'utente.  
  
     In questo approccio, il programma di installazione è responsabile della determinazione della versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e inclusi nella voce del Registro di sistema per l'associazione del file. In un pacchetto Windows Installer, è possibile includere azioni personalizzate per impostare una proprietà che indica la versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  In questo contesto, "più recente" significa "più recente versione supportata." Queste voci del programma di installazione non rileva automaticamente una versione successiva [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le voci in [requisiti di sistema di rilevamento](../extensibility/internals/detecting-system-requirements.md) e [comandi che devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md) sono simili a quelle fornite in questa sezione e sono necessarie per supportare versioni aggiuntive di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Le righe seguenti nella tabella CustomAction impostare la proprietà DEVENV_EXE_LATEST sia una proprietà di impostazione di AppSearch e tabelle RegLocator illustrate in [comandi che devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md). Le righe della tabella InstallExecuteSequence pianificare le azioni personalizzate nelle prime fasi della sequenza di esecuzione. I valori nel rendere colonna condizione la logica di lavoro:  
  
    -   Visual Studio .NET 2002 è la versione più recente, se si tratta della versione solo presente.  
  
    -   Visual Studio .NET 2003 è la versione più recente solo se è presente e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è presente.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Se si tratta della versione solo presente, è la versione più recente.  
  
     Il risultato è che DEVENV_EXE_LATEST contiene il percorso della versione più recente di devenv.exe.  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Righe della tabella CustomAction determinano la versione più recente di Visual Studio  
  
    |Operazione|Tipo|Origine|destinazione|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Righe della tabella InstallExecuteSequence che determinano la versione più recente di Visual Studio  
  
    |Operazione|Condizione|Sequence|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 E NON (DEVENV_EXE_2003 O DEVENV_EXE_2005)|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 E NON DEVENV_EXE_2005|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     È possibile utilizzare la proprietà DEVENV_EXE_LATEST nella tabella del Registro di sistema del pacchetto Windows Installer per scrivere il HKEY_CLASSES_ROOT*ProgId*valore predefinito della chiave ShellOpenCommand [DEVENV_EXE_LATEST] "%1"  
  
-   Eseguire un programma di avvio condiviso che può adottare la scelta migliore rispetto alle versioni VSPackage disponibili.  
  
     Gli sviluppatori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] scelto questo approccio per gestire i requisiti dei formati di soluzioni e progetti risultanti da molte versioni di più complessi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In questo approccio, si registra un programma di avvio come il gestore dell'estensione. L'utilità di avvio esamina il file e decide quale versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il pacchetto VSPackage può gestire il file in questione. Ad esempio, se un utente apre un file che è stato salvato per una particolare versione di un VSPackage, l'utilità di avvio può avviare tale pacchetto VSPackage nella versione corrispondente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Inoltre, un utente è stato possibile configurare l'utilità di avvio per avviare sempre la versione più recente. Un'utilità di avvio, inoltre, potrebbe richiedere un utente di aggiornare il formato del file. Se il formato del file include un numero di versione, l'utilità di avvio potrebbe informare un utente se il formato di file da una versione successiva di uno o più dei VSPackage installati.  
  
     L'utilità di avvio deve essere in un componente di Windows Installer è condiviso con tutte le versioni di un VSPackage. Questo processo consente di verificare che la versione più recente viene sempre installata e non viene rimosso fino a quando non vengono disinstallate tutte le versioni di un VSPackage. In questo modo, le associazioni di file e le altre voci del Registro di sistema del componente dell'utilità di avvio vengono mantenuti, anche se si disinstalla una versione del pacchetto VSPackage.  
  
## <a name="uninstall-and-file-associations"></a>Disinstallare e le associazioni di File  
 La disinstallazione di un VSPackage che scrive le voci del Registro di sistema per le associazioni di file consente di rimuovere le associazioni di file. Pertanto, l'estensione non ha programmi associati. Windows Installer non "Ripristina" le voci del Registro di sistema che sono stati aggiunti durante l'installazione di VSPackage. Di seguito sono riportati alcuni modi per risolvere le associazioni di file dell'utente:  
  
-   Utilizzare un componente condiviso dell'utilità di avvio come descritto in precedenza.  
  
-   Chiedere all'utente di eseguire un ripristino della versione del pacchetto VSPackage che l'utente desidera proprietari l'associazione del file.  
  
-   Specificare un programma eseguibile distinto che riscrive le voci del Registro di sistema appropriati.  
  
-   Fornire una configurazione opzioni pagina o finestra di dialogo che consente agli utenti di scegliere le associazioni di file e recuperare le associazioni perse. Indicare agli utenti di eseguirlo dopo la disinstallazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)