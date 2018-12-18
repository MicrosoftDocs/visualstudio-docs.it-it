---
title: Profilatura su cluster HPC (High Performance Computing) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53fea09175d9d9653dd4552832cd511ed7900b8e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>Profilatura su cluster HPC (High Performance Computing)
È possibile eseguire la profilatura sui nodi di calcolo di cluster Microsoft Windows HPC tramite il metodo di campionamento degli strumenti di profilatura di [!INCLUDE[vsPreExt](../profiling/includes/vspreext_md.md)] o [!INCLUDE[vsUltExt](../profiling/includes/vsultext_md.md)]. Per altre informazioni su HPC, vedere [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) nel sito Web Microsoft.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire la profilatura su un nodo di calcolo HPC, è necessario eseguire le operazioni seguenti:  
  
-   Installare Microsoft HPC Pack 2008 nello stesso computer di [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]. Il computer non deve far parte del cluster HPC. È possibile installare HPC Pack nell'[Area download Microsoft](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
-   Installare [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] e la versione autonoma degli strumenti di profilatura sul nodo di calcolo HPC. I programmi di installazione per [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e per il profiler autonomo sono disponibili nel supporto di installazione di [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]. **Nota** È necessario riavviare il computer dopo avere installato [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e prima di installare gli strumenti di profilatura.  
  
 Per installare [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] e gli strumenti di profilatura autonomi su un nodo di calcolo HPC attivo e abilitare la profilatura nel computer del cluster, attenersi alla procedura seguente:  
  
1.  Aprire la finestra del prompt dei comandi installata con HPC Pack.  
  
2.  Digitare i comandi seguenti in prompt dei comandi distinti:  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Nome del nodo head del cluster.|  
|*%FxPath%*|Percorso del programma di installazione di [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)]. Nel supporto di installazione di [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] il percorso è: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*%ProfilerPath%*|Percorso della versione autonoma del programma di installazione degli strumenti di profilatura. Nel supporto di installazione di [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] il percorso è: Standalone Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>Esecuzione della profilatura su un nodo di calcolo HPC  
 È possibile configurare una sessione di profilatura tramite la Creazione guidata sessione di prestazioni HPC per specificare informazioni sul cluster HPC e sulla destinazione. Eventuali opzioni aggiuntive possono essere impostate nelle pagine delle proprietà della sessione di prestazioni. Gli strumenti di profilatura distribuiscono automaticamente i file binari di destinazione necessari e avviano il profiler e l'applicazione HPC.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Per eseguire la profilatura su un nodo di calcolo HPC  
  
1.  Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni HPC**. Se il comando non è disponibile, assicurarsi di disporre dei prerequisiti elencati in precedenza.  
  
2.  Fare clic su **Avanti** nella prima pagina della procedura guidata.  
  
3.  Nella seconda pagina della procedura guidata selezionare l'applicazione da profilare.  
  
    -   Per profilare un progetto attualmente aperto in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], selezionare l'opzione **Uno o più progetti disponibili** e quindi selezionare il nome del progetto dall'elenco.  
  
    -   Per profilare un file binario non incluso in un progetto aperto, selezionare l'opzione **Eseguibile (file EXE)**.  
  
4.  Scegliere **Avanti**.  
  
5.  Nella terza pagina della procedura guidata:  
  
    -   Se si profila un file eseguibile non incluso in un progetto aperto, specificare il percorso del file binario in **Specificare il percorso completo dell'eseguibile**.  
  
    -   Se si profila un file eseguibile non incluso in un progetto aperto, è possibile specificare qualsiasi argomento della riga di comando da passare al processo in **Argomenti della riga di comando**.  
  
    -   In **Cartella di lavoro remota** specificare il percorso della cartella usata dalle istanze del processo sui singoli nodi di calcolo.  
  
    -   In **Percorso di distribuzione** specificare il percorso della directory usata dal server HPC per la gestione temporanea di immagini per la distribuzione.  
  
6.  Scegliere **Avanti**.  
  
7.  Nella quarta pagina della procedura guidata:  
  
    -   Nell'elenco **Nodo Head** fare clic sul computer che funge da nodo head HPC nell'esecuzione della profilatura. Il nodo head può essere "localhost", in modo da consentire l'esecuzione della profilatura nel computer locale senza la necessità di un cluster.  
  
    -   Nell'elenco **Numero di processi** fare clic sul numero di istanze dell'applicazione da eseguire.  
  
    -   Nell'elenco **Opzioni profilatura** selezionare la destinazione di profilatura.  
  
         Per profilare un processo specifico nel cluster, selezionare l'opzione **Esegui profilatura su priorità** e quindi selezionare la priorità del processo nell'elenco a discesa.  
  
         Per profilare il processo o i processi eseguiti su un nodo specifico nel cluster HPC, selezionare l'opzione **Esegui profilatura su nodo** e quindi selezionare il nodo nell'elenco a discesa.  
  
8.  Scegliere **Avanti**.  
  
9. Nella quinta pagina della procedura guidata è possibile scegliere di avviare immediatamente il profiler e il processo di profilatura oppure di avviare la profilatura in un secondo momento tramite Esplora prestazioni.  
  
    -   Selezionare **Avvia profilatura al termine della procedura guidata** per avviare la profilatura immediatamente oppure deselezionare la casella di controllo per avviare la profilatura manualmente.  
  
10. Scegliere **Fine**.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Impostazione delle proprietà di profilatura HPC tramite le pagine delle proprietà della sessione di prestazioni  
 È possibile modificare le proprietà della sessione di prestazioni impostate nella procedura guidata di profilatura HPC nella pagina Proprietà avvio HPC della pagina delle proprietà della sessione di prestazioni. Le opzioni aggiuntive vengono impostate nella pagina Proprietà avanzate HPC.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>Per aprire le pagine delle proprietà della sessione di prestazioni  
  
1.  Se necessario, aprire il file della sessione di prestazioni (con estensione psess) in Esplora prestazioni. Scegliere **Apri** dal menu **File** e individuare il file.  
  
2.  In Esplora prestazioni fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo Pagine delle proprietà usare uno dei metodi seguenti:  
  
    -   Fare clic su **Generale** e quindi selezionare **Raccolta su cluster HPC** per attivare la profilatura HPC oppure deselezionare la casella di controllo per disabilitarla.  
  
    -   Fare clic su **Proprietà avvio HPC** per modificare le proprietà di avvio dell'applicazione HPC.  
  
    -   Fare clic su **Proprietà avanzate HPC** per impostare opzioni aggiuntive.  
  
### <a name="hpc-launch-properties"></a>Proprietà avvio HPC  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Nodo head**|Specifica il computer che funge da nodo head HPC nell'esecuzione della profilatura.|  
|**Numero di processi**|Specifica il numero di istanze dell'applicazione da eseguire nell'applicazione profilata.|  
|**Esegui profilatura su priorità**|Per profilare un processo specifico nel cluster, selezionare l'opzione **Esegui profilatura su priorità** e quindi selezionare la priorità del processo nell'elenco a discesa.|  
|**Esegui profilatura su nodo**|Per profilare il processo o i processi eseguiti su un nodo specifico nel cluster HPC, selezionare l'opzione **Esegui profilatura su nodo** e quindi selezionare il nodo nell'elenco a discesa.|  
|**Cartella di lavoro remota**|Specifica il percorso della cartella usata dalle istanze del processo sui singoli nodi di calcolo.|  
|**Percorso di distribuzione**|Specifica il percorso della directory usata dal server HPC per la gestione temporanea di immagini per la distribuzione.|  
  
### <a name="advanced-properties"></a>Proprietà avanzate  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Nome progetto**|Nome del progetto o della soluzione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] corrente.|  
|**Esegui pulizia all'arresto del profiler**|Se il valore è true, rimuove i file binari distribuiti alla directory di esecuzione. I file e le directory creati dal programma utente non vengono rimossi in questo passaggio. Se la directory di esecuzione e la directory di distribuzione sono state create dall'IDE, l'IDE stesso tenterà di rimuoverle, a meno che non contengano file non distribuiti dall'IDE.|  
|**File aggiuntivi da distribuire**|Specifica un elenco di file aggiuntivi separati da punto e virgola da distribuire sul nodo di calcolo. È possibile fare clic sul pulsante con i puntini di sospensione (**...**) per selezionare più file usando una finestra di dialogo.|  
|**Comando Mpiexec**|Specifica l'applicazione che avvia l'applicazione MPI. Il valore predefinito è **mpiexec.exe**.|  
|**Argomenti Mpiexec**|Specifica gli argomenti da passare al comando mpiexec.exe.|  
|**Nodi richiesti nel cluster**|Specifica il numero di nodi nel cluster su cui eseguire l'applicazione.|  
|**Distribuisci file CRT**|Se il valore è true, distribuisce il runtime C/C++ nel cluster.|  
|**Script pre-profilatura**|Specifica il percorso e il nome file di uno script da eseguire nel computer di sviluppo locale prima dell'avvio della sessione di profilatura.|  
|**Argomenti script pre-profilatura**|Specifica gli argomenti da passare allo script pre-profilatura.|  
|**Script post-profilatura**|Specifica il percorso e il nome file di uno script da eseguire nel computer di sviluppo locale al termine della sessione di profilatura.|  
|**Argomenti script post-profilatura**|Specifica gli argomenti da passare allo script post-profilatura.|