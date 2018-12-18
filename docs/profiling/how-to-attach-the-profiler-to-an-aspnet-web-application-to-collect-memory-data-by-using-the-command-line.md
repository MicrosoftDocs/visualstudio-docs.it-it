---
title: "Procedura: Connettere il profiler a un'applicazione Web ASP.NET per raccogliere dati di memoria tramite la riga di comando | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: e45eb3e1ac874343de5a3076a62b89e541f20d75
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Procedura: connettere il profiler a un'applicazione Web ASP.NET per raccogliere dati di memoria tramite la riga di comando
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e raccogliere dati sul numero e le dimensioni delle allocazioni di memoria .NET Framework. È anche possibile raccogliere dati sulla durata degli oggetti di memoria di .NET Framework.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere dati sulle prestazioni da un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è necessario usare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate nel computer che ospita l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. È quindi necessario riavviare il computer per configurare il server Web per la profilatura.  
  
 Usare quindi lo strumento [VSPerfCmd.exe](../profiling/vsperfcmd.md) per connettere il profiler al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] che ospita il sito Web. Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.  
  
 Per terminare una sessione di profilatura, il profiler non deve essere più connesso all'applicazione e deve essere arrestato in modo esplicito. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.  
  
## <a name="attaching-the-profiler"></a>Connessione del profiler  
  
#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Per connettere il profiler a un'applicazione Web ASP.NET  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Inizializzare le variabili di ambiente di profilatura. Tipo:  
  
     **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]  
  
    -   Le opzioni **/globalsamplegc** e **/globalsamplegclife** specificano il tipo di dati di memoria da raccogliere.  
  
         Specificare una sola delle opzioni seguenti.  
  
        |Opzione|Descrizione|  
        |------------|-----------------|  
        |**/globalsamplegc**|Abilita la raccolta dei dati di allocazione della memoria.|  
        |**/globalsamplegclife**|Abilita la raccolta dei dati di allocazione della memoria e dei dati di durata degli oggetti.|  
  
    -   L'opzione **/samplelineoff** disabilita l'assegnazione dei dati raccolti a righe specifiche del codice sorgente. Quando viene specificata questa opzione, i dati vengono assegnati a livello di funzione.  
  
3.  Riavviare il computer per impostare la nuova configurazione di ambiente.  
  
4.  Aprire una finestra del prompt dei comandi. Se necessario, impostare la variabile di ambiente del percorso del profiler.  
  
5.  Avvia il profiler. Tipo:  
  
     **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   L'opzione **/start:sample** inizializza il profiler.  
  
    -   L'opzione **/output:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:sample**.  
  
    > [!NOTE]
    >  Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni di accesso. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'identificatore di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**.|  
    |[/waitstart](../profiling/waitstart.md) [**:**`Interval`]|Specifica il numero di secondi di attesa dell'inizializzazione del profiler prima che venga restituito un errore. Se `Interval` non viene specificato, il profiler attende per un tempo indefinito. Per impostazione predefinita, **/start** restituisce immediatamente un valore.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
6.  Avviare l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nel modo usuale.  
  
7.  Connettere il profiler al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Tipo:  
  
     **VSPerfCmd**  [/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   L'ID processo `(PID)` specifica l'ID o il nome del processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   **/targetclr:** `Version` specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione.  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Quando è in esecuzione l'applicazione, è possibile controllare la raccolta dei dati avviando e arrestando la scrittura dei dati nel file di dati del profiler usando le opzioni di **VSPerfCmd.exe**. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le seguenti coppie di opzioni **VSPerfCmd** consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o arresta (**/processoff**) la raccolta dei dati per il processo specificato da `PID`.|  
    |**/attach:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;:`ProcName`}]|**/attach** avvia la raccolta dei dati per il processo specificato dall'ID o dal nome di processo. **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, è necessario disconnettere il profiler dall'applicazione Web. È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di campionamento riavviando il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o chiamando l'opzione **VSPerfCmd /detach**. Chiamare quindi l'opzione **VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura, ma la configurazione di sistema non viene reimpostata fino al riavvio del computer.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Digitare **VSPerfCmd** [/detach](../profiling/detach.md)  
  
         oppure  
  
    -   Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Tipo:  
  
     **IISReset /stop**  
  
2.  Arrestare il profiler. Tipo:  
  
     **VSPerfCmd /shutdown**  
  
3.  (Facoltativo) Cancellare le variabili di ambiente di profilatura. Tipo:  
  
     **VSPerfCmd /globaloff**  
  
4.  Riavviare il computer. Se necessario, riavviare Internet Information Services (IIS). Tipo:  
  
     **IISReset /start**  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)