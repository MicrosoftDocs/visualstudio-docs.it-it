---
title: 'Procedura: Avviare un''applicazione nativa autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: deaed7caedfa825917d4d6740f3d1866f77da68e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Procedura: avviare un'applicazione nativa autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare un'applicazione (client) autonoma nativa e raccogliere dati di concorrenza di thread e processi.  
  
 Una sessione di profilatura si articola nelle seguenti parti:  
  
-   Avvio dell'applicazione con il profiler  
  
-   Controllo della raccolta di dati  
  
-   Arresto della sessione di profilatura  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare il profiler da un prompt dei comandi, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra **Prompt dei comandi** oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="starting-the-application-with-the-profiler"></a>Avvio dell'applicazione con il profiler  
 Per avviare un'applicazione di destinazione con il profiler, usare le opzioni [VSPerfCmd.exe](../profiling/vsperfcmd.md)**/start** e **/launch** per inizializzare il profiler e avviare l'applicazione. È possibile specificare **/start** e **/launch** e le relative opzioni. È anche possibile aggiungere l'opzione **/globaloff** per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione. Usare quindi **/globalon** per iniziare a raccogliere i dati.  
  
#### <a name="to-start-an-application-with-the-profiler"></a>Per avviare un'applicazione con il profiler  
  
1.  Digitare il comando seguente al prompt dei comandi:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]  
  
     L'opzione [/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare una qualsiasi delle opzioni nella tabella seguente con l'opzione **/start:concurrency**.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
2.  Avviare l'applicazione di destinazione digitando:  
  
     **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `AppName` [`Options`]  
  
     È possibile usare una qualsiasi delle opzioni nella tabella seguente con l'opzione **/launch**.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/args](../profiling/args.md) **:** `Arguments`|Specifica una stringa che contiene gli argomenti della riga di comando da passare all'applicazione di destinazione.|  
    |[/console](../profiling/console.md)|Avvia l'applicazione della riga di comando di destinazione in una finestra separata.|  
    |[/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Specifica la versione di Common Language Runtime (CLR) da profilare se l'applicazione carica più di una versione di CLR.|  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file con le opzioni VSPerfCmd.exe. Per controllare la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le coppie di opzioni nella tabella seguente consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID di processo (`PID`) o dal nome di processo (*ProcName*). **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo.|  
  
-   È anche possibile usare l'opzione **VSPerfCmd.exe**[/mark](../profiling/mark.md) per inserire un indicatore di profilatura nel file di dati. Il comando **/mark** aggiunge un identificatore, un timestamp e una stringa di testo facoltativa definita dall'utente. Gli indicatori possono essere usati per filtrare i dati nei rapporti e nelle visualizzazioni dei dati del profiler.  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, non deve essere in corso una raccolta di dati dal profiler. È possibile interrompere la raccolta dei dati di concorrenza chiudendo l'applicazione profilata o richiamando l'opzione **VSPerfCmd /detach**. È quindi possibile richiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Disconnettere il profiler dall'applicazione di destinazione chiudendola o digitando il comando seguente al prompt dei comandi:  
  
     **VSPerfCmd /detach**  
  
2.  Arrestare il profiler digitando il comando seguente al prompt dei comandi:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)