---
title: Panoramica sulle opzioni di configurazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edfe84e26a9331b8c40ec24b00387768bdbba82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-options-overview"></a>Cenni preliminari sulle opzioni di configurazione
I progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può supportare più configurazioni che possono essere compilate in fase di debug, esecuzione e/o distribuiti. Una configurazione è un tipo di compilazione descritto, con un set denominato di proprietà, in genere le opzioni del compilatore e percorsi dei file. Per impostazione predefinita, le nuove soluzioni contengono due configurazioni, Debug e rilascio. Possono applicare queste configurazioni utilizzando le impostazioni predefinite o modificare per soddisfare i requisiti della soluzione e/o di progetto specifici. Alcuni pacchetti possono essere compilati in due modi: come un editor di ActiveX o come un componente sul posto. I progetti non è necessario supportare più configurazioni, è tuttavia. Se è disponibile solo una configurazione, viene eseguito il mapping di tale configurazione in tutte le configurazioni di soluzione.  
  
 Le configurazioni in genere costituiti da due parti, ovvero il nome della configurazione (ad esempio Debug o Release) e impostazioni piattaforma. Nome di una configurazione piattaforma identifica l'ambiente in cui impostare le destinazioni di configurazione, ad esempio un'API o piattaforma del sistema operativo. Gli utenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è possibile creare una piattaforma; devono scegliere dalle selezioni un progetto consente di VSPackage. Quando un utente installa un pacchetto VSPackage, la piattaforma di distribuzione creata durante lo sviluppo del pacchetto, può verificarsi qualsiasi nome di piattaforma desiderato in base a qualsiasi criteri impostati dall'autore del pacchetto. L'utente può quindi selezionare dall'elenco di piattaforme resi disponibili tramite il pacchetto VSPackage quando viene creata un'istanza le pagine delle proprietà.  
  
 Poiché non tutti i progetti supportano il concetto di piattaforme, i nomi di piattaforma sono facoltativi. Quando una configurazione non dispone di un nome di piattaforma, la stringa "n/d" viene visualizzato nell'interfaccia utente.  
  
 Ogni soluzione ha un proprio set di configurazioni, solo uno dei quali può essere attivo alla volta. Una configurazione di soluzione è un set di non più di una configurazione di ogni progetto. Il criterio "non maggiore di" fa è dovuto all'opzione per escludere un progetto da una configurazione di soluzione. Gli utenti possono creare configurazioni di soluzione personalizzata.  
  
 Nella tabella seguente viene illustrato il programma di installazione di configurazioni tipiche per un progetto. Le righe vengono identificate con nomi di configurazione e le colonne con nomi di piattaforma.  
  
|Nome della configurazione|Piattaforma, Win32|Piattaforma: Win64|  
|------------------------|----------------------|----------------------|  
|Debug|\<Eseguire il debug Win32 Impostazioni >|\<Debug impostazioni Win64 >|  
|Rilascio|\<Versione Win32 Impostazioni >|\<Versione Win64 Impostazioni >|  
|MyConfig|N/D|\<Impostazioni MyConfig Win64 >|  
  
> [!NOTE]
>  È possibile creare una configurazione di soluzione "MyConfig" che esclude una piattaforma "Win32", a meno che il progetto di destinazione non supporta Win32.  
  
 Modifica la configurazione attiva per una soluzione consente di selezionare il set di configurazioni di progetto che vengono compilate, esecuzione, eseguire il debug o distribuiti all'interno della soluzione. Ad esempio, se si modifica la configurazione di soluzione attiva dalla versione di Debug, tutti i progetti contenuti nella soluzione vengono compilati automaticamente con la configurazione del progetto indicato nella configurazione di Debug della soluzione. Le configurazioni del progetto sono in genere denominata Debug a meno che l'utente ha apportato modifiche manuali dell'ambiente di Configuration Manager.  
  
 Le proprietà di configurazione di soluzione archiviate per ogni progetto includono il nome del progetto, nome configurazione progetto, i flag per indicare se per compilare o distribuire e il nome della piattaforma. Per ulteriori informazioni, vedere [configurazione soluzione](../../extensibility/internals/solution-configuration.md).  
  
 L'utente può visualizzare e impostare parametri di configurazione di soluzione, la scelta della soluzione nella gerarchia (Esplora soluzioni) e aprire le pagine delle proprietà. Analogamente, è possibile visualizzare e impostare i parametri di configurazione di progetto, selezionare un progetto in Esplora soluzioni e aprire le pagine delle proprietà del progetto.  
  
 L'utente è anche possibile creare un progetto utilizzando le impostazioni di configurazione di rilascio e tutte le altre con le impostazioni di configurazione di Debug, se necessario. Per ulteriori informazioni, vedere [configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).  
  
 Il diagramma seguente illustra le modalità di implementazione delle interfacce che supportano le configurazioni di soluzione e progetto:  
  
 ![Rappresentazione grafica delle interfacce di configurazione](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfacce di configurazione  
  
 Alcune note relative al diagramma precedente:  
  
-   `IDispatch`è contrassegnato come facoltativi nell'oggetto di configurazione. In particolare, è facoltativo per le interfacce di configurazione per l'oggetto visualizzazione.  
  
-   `IVsDebuggableProjectCfg`è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto di debug.  
  
-   `IVsProjectCfg2`è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per l'output del supporto di raggruppamento.  
  
-   Il `Config Provider` oggetto viene contrassegnato come un oggetto facoltativo, ma l'opzione è la posizione in cui implementarla. È possibile implementare l'oggetto per l'oggetto di progetto o in un oggetto separato.  
  
-   `IVsCfgProvider2`è necessario per il supporto di piattaforma e la modifica della configurazione. `IVsCfgProvider`è sufficiente se non si implementa la funzionalità.  
  
-   Alcuni di questi oggetti illustrati nel diagramma come oggetti distinti possono essere combinati nella stessa classe dove possibile in base ai requisiti di progettazione specifica. In altri argomenti di questa sezione, tuttavia, gli oggetti e interfacce associate a tali oggetti verranno analizzate in base allo scenario presentato nel diagramma.  
  
-   Alcuni oggetti vengono implementati separatamente. Ad esempio, progetto e soluzione compilazione si verificano nel thread distinti e l'oggetto per la gestione della qualità della vita compilazione separatamente dall'oggetto che descrive la configurazione per la compilazione.  
  
 Per ulteriori informazioni sulle interfacce dell'oggetto di configurazione e le interfacce di oggetto Provider di configurazione nel diagramma precedente, vedere [oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md). Inoltre, [configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md) vengono fornite ulteriori informazioni sulle interfacce generatore di configurazione e l'oggetto di dipendenza di compilazione, e [configurazione di progetto per la Gestione distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md) Descrive ulteriormente le interfacce collegate al deployer di configurazione e distribuzione di oggetti di dipendenza. Infine, [configurazione di progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md) descrive le interfacce dell'oggetto di Output e di gruppo di Output e l'utilizzo delle pagine delle proprietà per visualizzare e impostare le proprietà dipendenti dalla configurazione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)