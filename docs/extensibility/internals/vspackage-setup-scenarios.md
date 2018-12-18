---
title: Gli scenari di installazione di VSPackage | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dea9d25f211ca5042234c0400b2a10086136f49c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-setup-scenarios"></a>Scenari di installazione di VSPackage
È importante per il programma di installazione del pacchetto VSPackage per offrire la flessibilità di progettazione. Ad esempio, potrebbe essere necessario rilasciare una patch di sicurezza in futuro oppure è possibile modificare una strategia aziendale che richiede il supporto completo controllo delle versioni side-by-side.  
  
 In [di supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), è possibile leggere sui vantaggi e i problemi di supporto installazioni side-by-side di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con installazioni condivise o side-by-side di VSPackage. In breve, VSPackage side-by-side offrono la massima flessibilità per supportare nuove funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Gli scenari illustrati in questo argomento non sono scelte sole, ma in cui vengono presentati come procedure consigliate.  
  
## <a name="components-privacy-and-sharing"></a>I componenti, Privacy e la condivisione  
  
##### <a name="make-your-components-independent"></a>Creazione di componenti indipendenti  
 Dopo avere identificato e compilare un componente, assegnare un `GUID`e distribuire il componente non è possibile modificare la composizione. Se si modifica una composizione di un componente, il componente risulta deve essere un nuovo componente con un nuovo `GUID`. Dato questi fatti, viene offerta la massima flessibilità per il controllo delle versioni, eseguendo ogni unità indipendente e radicato del componente. Per ulteriori informazioni sulle regole che governano i componenti, vedere [la modifica del codice del componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) e [cosa accade se le regole di componente vengono interrotti?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Non combinare risorse condivise e private in un componente  
 Il conteggio dei riferimenti si verifica a livello di componente. Di conseguenza, la combinazione di risorse condivise e private in un componente non consente di aggiornare le risorse private, ad esempio un file eseguibile, senza sovrascrivere anche le risorse condivise. Questo scenario consente di creare problemi di compatibilità e si impedisce la creazione di funzionalità side-by-side.  
  
 Ad esempio, i valori del Registro di sistema utilizzato per registrare il pacchetto VSPackage con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] deve essere conservata in un componente separato da quello utilizzato per registrare il pacchetto VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. I valori del Registro di sistema o file condivisi inseriti in un altro componente.  
  
## <a name="scenario-1-shared-vspackage"></a>Scenario 1: Condiviso VSPackage  
 In questo scenario, un package VS condivisi (un singolo binario che supporta più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) viene fornito in un pacchetto Windows Installer. Registrazione con ogni versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dipende dalle funzionalità selezionabili dall'utente. Significa anche che quando assegnato per separare le funzionalità, ogni componente può essere selezionato singolarmente per l'installazione o la disinstallazione, inserisce l'utente nel controllo di integrazione di VSPackage in versioni diverse di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Vedere [funzionalità di Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) per ulteriori informazioni sull'utilizzo delle funzionalità nei pacchetti di Windows Installer.)  
  
 ![Rappresentazione grafica VS package VS condivisi](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")  
Programma di installazione di package VS condiviso  
  
 Come illustrato nella figura, i componenti condivisi diventano parte della funzionalità di Feat_Common, viene sempre installata. Per rendere visibili le funzionalità di Feat_VS2002 e Feat_VS2003, gli utenti possono scegliere al momento dell'installazione in quali versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desiderano VSPackage per l'integrazione. Gli utenti possono inoltre utilizzare modalità di manutenzione di Windows Installer per aggiungere o rimuovere funzionalità, che in questo caso aggiunge o rimuove le informazioni di registrazione del pacchetto VSPackage di versioni diverse di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Colonna di visualizzazione di una funzionalità di impostazione su 0 la nasconde. Un valore di colonna di livello basso, ad esempio 1, garantisce che sarà sempre installata. Per ulteriori informazioni, vedere [proprietà INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) e [tabella delle funzionalità](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scenario 2: Aggiornamento di package VS condivisi  
 In questo scenario, è disponibile una versione aggiornata del programma di installazione di VSPackage nello scenario 1. Ai fini di discussione, l'aggiornamento aggiunge il supporto per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ma potrebbe anche essere un semplice sicurezza patch o correzione di bug service pack. Regole del programma di installazione di Windows per l'installazione dei componenti più recenti richiedono che invariati componenti già installati nel sistema vengono ricopiati non. In questo caso, un sistema con la versione 1.0 sono già presenti verrà sovrascriverà il componente aggiornato Comp_MyVSPackage.dll e consentire agli utenti di scegliere di aggiungere la nuova funzionalità Feat_VS2005 con il componente relativo Comp_VS2005_Reg.  
  
> [!CAUTION]
>  Ogni volta che un VSPackage è condiviso tra più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è essenziale che le versioni successive di VSPackage mantengono la compatibilità con le versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. In cui è possibile mantenere la compatibilità con le versioni precedenti, è necessario utilizzare VSPackage side-by-side e privati. Per ulteriori informazioni, vedere [di supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Immagine dell'aggiornamento Package VS condivisi](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Programma di installazione aggiornamento package VS condivisi  
  
 Questo scenario viene presentato un nuovo pacchetto VSPackage programma di installazione, sfruttando la possibilità di supporto del programma di installazione di Windows per aggiornamenti secondari. Gli utenti è sufficiente installano la versione 1.1 e viene aggiornato alla versione 1.0. Non è tuttavia necessario che la versione 1.0 nel sistema. Lo stesso di installazione installerà la versione 1.1 in un sistema senza versione 1.0. Il vantaggio di fornire aggiornamenti secondari in questo modo è che non è necessario eseguire le operazioni di sviluppo di un programma di installazione dell'aggiornamento e un programma di installazione del prodotto completo. Un programma di installazione esegue entrambi i processi. Una correzione per la protezione o un servizio di tipo pack potrebbe invece sfruttare le patch di Windows Installer. Per ulteriori informazioni, vedere [l'applicazione di patch e aggiornamenti](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scenario 3: Side-by-Side VSPackage  
 Due programmi di installazione di VSPackage presentato in questo scenario, uno per ogni versione di Visual Studio .NET 2003 e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ogni programma di installazione installa un side-by-side privato, VSPackage (uno in modo specifico compilato e installato per una particolare versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]). Ogni pacchetto VSPackage è proprio componente. Di conseguenza, ogni possibile singolarmente servite con patch o di manutenzione rilascia. Poiché la DLL VSPackage è ora specifico della versione, è possibile includere le informazioni di registrazione nello stesso componente della DLL.  
  
 ![Sul lato di Visual Studio &#45; da &#45; Immagine di Package VS lato](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")  
Programma di installazione side-by-side VSPackage  
  
 Ogni programma di installazione include anche il codice è condiviso tra i due programmi di installazione. Se il codice condiviso viene installato in un percorso comune, entrambi i file con estensione msi di installazione installerà il codice condiviso una sola volta. Il programma di installazione secondo incrementa semplicemente un conteggio dei riferimenti del componente. Il conteggio dei riferimenti garantisce che se uno dei VSPackage viene disinstallato, il codice condiviso resterà per altri VSPackage. Se il pacchetto VSPackage secondo viene disinstallato anche, verrà rimosso il codice condiviso.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenario 4: Side-by-Side VSPackage aggiornamento  
 In questo scenario, il pacchetto VSPackage per [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] subito dalla protezione di una vulnerabilità ed è necessario eseguire un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file con estensione msi che aggiorna un'installazione esistente per includere la correzione di sicurezza, nonché di distribuire le nuove installazioni con la correzione di sicurezza già presenti.  
  
 In questo caso, il pacchetto VSPackage è un pacchetto VSPackage gestito installato nella global assembly cache (GAC). Durante la ricompilazione includono la correzione di sicurezza, è necessario modificare la parte del numero di revisione del numero di versione di assembly. Le informazioni di registrazione per il nuovo numero di versione di assembly sovrascriverà la versione precedente, causando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per caricare l'assembly predefinito.  
  
 ![Sul lato di Visual Studio &#45; da &#45; Immagine di aggiornamento del pacchetto VS lato](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")  
Programma di installazione aggiornamento side-by-side VSPackage  
  
 **Nota** per ulteriori informazioni sulla distribuzione di assembly side-by-side, vedere [semplificando la distribuzione e la risoluzione di DLL Hell con .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)