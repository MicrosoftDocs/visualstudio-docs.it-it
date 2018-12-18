---
title: 'Procedura dettagliata: profilatura dalla riga di comando tramite campionamento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 403e685fa6a386ea0de73c74a27261d9ab77786e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento
Questa procedura dettagliata illustra come eseguire la profilatura di un'applicazione mediante gli strumenti da riga di comando e il campionamento per identificare i problemi di prestazioni.  
  
 In questa procedura dettagliata verrà illustrato il processo di profilatura di un'applicazione gestita tramite gli strumenti da riga di comando e sarà descritto come usare il campionamento per isolare e identificare i problemi di prestazioni nell'applicazione.  
  
 In questa procedura dettagliata vengono illustrate le operazioni seguenti:  
  
-   Eseguire la profilatura di un'applicazione usando gli strumenti della riga di comando e il campionamento.  
  
-   Analizzare i risultati della profilatura campionati per individuare e risolvere i problemi di prestazioni.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Conoscenza a livello intermedio di [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]  
  
-   Conoscenza a livello intermedio dell'uso degli strumenti della riga di comando  
  
-   Una copia dell'[esempio PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Per usare le informazioni fornite dalla profilatura, è consigliabile avere a disposizione informazioni sui simboli di debug.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Profilatura dalla riga di comando tramite il metodo di campionamento  
 Il campionamento è un metodo di profilatura mediante il quale viene eseguito periodicamente il polling di un processo specifico per determinare la funzione attiva. I dati risultanti forniscono un conteggio della frequenza con cui la funzione si trovava all'inizio dello stack di chiamate quando è stato eseguito il campionamento del processo.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli Strumenti di Profilatura sono contenuti nella sottodirectory \Team Tools\Performance Tools della directory di installazione di Visual Studio. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra Prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax è un'applicazione a 32 bit.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Per eseguire la profilatura dell'applicazione PeopleTrax tramite il metodo di campionamento  
  
1.  Installare l'applicazione di esempio PeopleTrax e compilare la versione di rilascio dell'applicazione.  
  
2.  Aprire una finestra del prompt dei comandi e aggiungere la directory degli strumenti di profilatura alla variabile di ambiente Path locale.  
  
3.  Cambiare la directory di lavoro, passando alla directory che contiene i file binari di PeopleTrax.  
  
4.  Digitare il comando seguente per impostare le variabili di ambiente appropriate:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5.  Avviare la profilatura eseguendo VSPerfCmd.exe, ovvero lo strumento da riga di comando che controlla il profiler. Il comando seguente avvia l'applicazione e il profiler in modalità di campionamento:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Il processo del profiler viene avviato e collegato al processo PeopleTrax.exe. Il processo del profiler inizia a scrivere i dati di profilatura raccolti nel file di report.  
  
6.  Fare clic su **Get People**.  
  
7.  Fare clic su **ExportData**.  
  
     Verrà aperto il Blocco note con un nuovo file che contiene i dati esportati da **PeopleTrax**.  
  
8.  Chiudere il Blocco note e quindi chiudere l'applicazione **PeopleTrax**.  
  
9. Arrestare il profiler. Digitare il comando seguente:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Usare il comando seguente per reimpostare le variabili di ambiente:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. I dati di profilatura vengono archiviati nel file con estensione vsp. Analizzare i risultati usando uno dei metodi seguenti:  
  
    -   Aprire il file con estensione vsp nell'IDE di Visual Studio.  
  
         oppure  
  
    -   Generare un file con valori delimitati da virgole (CSV) tramite lo strumento da riga di comando VSPerfReport.exe. Per generare report da usare all'esterno dell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], usare il comando seguente:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Performance Report Views](../profiling/performance-report-views.md)(Visualizzazioni dei rapporti di prestazioni)