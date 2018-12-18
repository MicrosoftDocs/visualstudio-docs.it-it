---
title: "Procedura: Connettere il profiler a un servizio nativo per raccogliere statistiche dell'applicazione tramite la riga di comando | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c61d95758597b09b28ee5acd6268c44ea1bf0869
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Procedura: connettere il profiler a un servizio nativo per raccogliere statistiche dell'applicazione tramite la riga di comando
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un servizio nativo e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Quando il profiler è connesso al servizio, è possibile sospendere e riprendere la raccolta dei dati.  
  
 Per terminare una sessione di profilatura, è necessario disconnettere il profiler dal servizio e arrestarlo in modo esplicito.  
  
## <a name="starting-the-application-with-the-profiler"></a>Avvio dell'applicazione con il profiler  
 Per connettere il profiler a un servizio nativo, usare le opzioni **VSPerfCmd.exe**[/start](../profiling/start.md) e [/attach](../profiling/attach.md) per inizializzare il profiler e connetterlo all'applicazione di destinazione. È possibile specificare **/start** e **/attach** e le relative opzioni in un'unica riga di comando. È anche possibile aggiungere l'opzione [/globaloff](../profiling/globalon-and-globaloff.md) per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione. Usare quindi [/globalon](../profiling/globalon-and-globaloff.md) per iniziare a raccogliere i dati.  
  
#### <a name="to-attach-the-profiler-to-a-native-service"></a>Per connettere il profiler a un servizio nativo  
  
1.  Se necessario, avviare il servizio.  
  
2.  Aprire una finestra del prompt dei comandi.  
  
3.  Avvia il profiler. Tipo:  
  
     **VSPerfCmd /start:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   L'opzione **/start:sample** inizializza il profiler.  
  
    -   L'opzione **/output:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:sample**.  
  
    > [!NOTE]
    >  Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per i servizi.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa. L'ID di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
4.  Connettere il profiler al servizio. Tipo:  
  
     **VSPerfCmd /attach:** `PID` [`Sample Event`]  
  
     `PID` specifica l'ID del processo dell'applicazione di destinazione. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
     Per impostazione predefinita, i dati relativi alle prestazioni vengono campionati ogni 10.000.000 di cicli di clock del processore non interrotti, ovvero circa una volta ogni 10 secondi in un processore da 1 GHz. È possibile specificare una delle opzioni seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso.  
  
    |Evento di campionamento|Descrizione|  
    |------------------|-----------------|  
    |[/timer](../profiling/timer.md) **:** `Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|  
    |[/pf](../profiling/pf.md)[**:**`Interval`]|Imposta l'evento di campionamento sugli errori di pagina. Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni. Il valore predefinito è 10.|  
    |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo (syscall). Se si specifica `Interval`, imposta il numero di chiamate tra campioni. Il valore predefinito è 10.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Imposta l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e sull'intervallo specificati in `Config`.|  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Mentre l'applicazione di destinazione è in esecuzione, è possibile usare le opzioni di **VSPerfCmd.exe** per avviare e arrestare la scrittura dei dati nel file di dati del profiler. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le seguenti coppie di opzioni **VSPerfCmd** consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID o dal nome di processo. **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo.|  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, è necessario disconnettere il profiler dal servizio e arrestarlo in modo esplicito. È possibile disconnettere il servizio nativo profilato con il metodo di campionamento interrompendo il servizio oppure chiamando l'opzione **VSPerfCmd /detach**. È quindi possibile chiamare l'opzione **VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Arrestare il servizio.  
  
         oppure  
  
    -   Digitare **VSPerfCmd /detach**  
  
2.  Arrestare il profiler. Tipo:  
  
     **VSPerfCmd /shutdown**  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)   
 [Sampling Method Data Views](../profiling/profiler-sampling-method-data-views.md) (Visualizzazioni dei dati del metodo di campionamento)