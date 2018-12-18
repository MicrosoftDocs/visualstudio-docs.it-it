---
title: "Procedura: Instrumentare un'applicazione Web ASP.NET compilata staticamente e raccogliere dati di memoria tramite la riga di comando del profiler | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76c9f5ca61c2950dfc2cc705a1e574e275ba1246
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Procedura: instrumentare un'applicazione Web ASP.NET compilata staticamente e raccogliere dati di memoria tramite la riga di comando del profiler
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un componente Web o un sito Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] precompilato e raccogliere dati di allocazione di memoria, di durata degli oggetti e di intervallo dettagliati .NET.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere dati da un componente Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando il metodo di strumentazione, usare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente. Nel computer che ospita il componente sostituire la versione non instrumentata del componente con la versione instrumentata. Usare quindi lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente di profilatura globali e riavviare il computer host. Avviare quindi il profiler.  
  
 Quando viene eseguito il componente instrumentato, i dati di intervallo vengono raccolti automaticamente in un file di dati. È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilatura.  
  
 Per terminare una sessione di profilatura, chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] che ospita il componente e quindi arrestare in modo esplicito il profiler. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.  
  
## <a name="starting-to-profile"></a>Avvio della profilatura  
  
#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Per instrumentare un componente Web ASP.NET e avviare la profilatura  
  
1.  Usare lo strumento **VSInstr** per generare una versione instrumentata dell'applicazione di destinazione. Se necessario, sostituire i file binari dell'applicazione nel computer host ASP.NET con i file binari instrumentati.  
  
2.  Aprire una finestra del prompt dei comandi  
  
3.  Inizializzare le variabili di ambiente di profilatura .NET. Nella finestra del prompt dei comandi digitare:  
  
     **VSPerfClrEnv /globaltracegc**  
  
     oppure  
  
     **VSPerfClrEnv /globaltracegclife**  
  
    -   **/globaltracegc** raccoglie i dati di allocazione della memoria e i dati di intervallo .NET.  
  
    -   **/globaltracegclife** raccoglie i dati di allocazione della memoria, di durata degli oggetti e di intervallo dettagliati .NET.  
  
4.  Riavviare il computer.  
  
5.  Aprire una finestra del prompt dei comandi.  
  
6.  Avvia il profiler. Nella finestra del prompt dei comandi digitare:  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   L'opzione [/start](../profiling/start.md)**:trace** consente di inizializzare il profiler.  
  
    -   L'opzione [/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:trace**.  
  
    > [!NOTE]
    >  Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Specifica il dominio facoltativo e il nome utente dell'account proprietario del processo di lavoro ASP.NET. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il nome è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa. L'ID di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **/globaloff** alla riga di comando **/start**. Usare **/globalon** per riprendere la profilatura.|  
  
7.  Aprire il sito Web che contiene il componente instrumentato.  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni **VSPerfCmd.exe**. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e quindi usare il comando **IISReset** di Internet Information Services (IIS) per chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Chiamare l'opzione **VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura. È necessario riavviare il computer per applicare le nuove impostazioni di ambiente.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Tipo:  
  
     **IISReset /stop**  
  
3.  Arrestare il profiler. Tipo:  
  
     **VSPerfCmd /shutdown**  
  
4.  (Facoltativo) Cancellare le variabili di ambiente di profilatura. Tipo:  
  
     **VSPerfCmd /globaloff**  
  
5.  Riavviare il computer. Se necessario, riavviare IIS. Tipo:  
  
     **IISReset /start**  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)