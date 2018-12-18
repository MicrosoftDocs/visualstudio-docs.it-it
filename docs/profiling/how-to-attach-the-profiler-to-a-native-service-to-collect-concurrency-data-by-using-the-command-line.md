---
title: 'Procedura: Connettere il profiler a un servizio nativo per raccogliere dati di concorrenza tramite la riga di comando | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d0906a567d71bb1f200803e1a3933ee7bad64f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Procedura: connettere il profiler a un servizio nativo per raccogliere dati di concorrenza tramite la riga di comando
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un servizio nativo (C/C++) e raccogliere dati di concorrenza di thread e processi tramite il metodo di campionamento.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli Strumenti di Profilatura sono contenuti nella sottodirectory \Team Tools\Performance Tools della directory di installazione di Visual Studio. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare il profiler da un prompt dei comandi, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra **Prompt dei comandi** o al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Quando il profiler è connesso al servizio, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura, il profiler non deve essere più connesso al servizio e deve essere arrestato in modo esplicito.  
  
## <a name="attaching-the-profiler"></a>Connessione del profiler  
 Per connettere il profiler a un servizio nativo, usare le opzioni **VSPerfCmd/start** e **/attach** per inizializzare il profiler e connetterlo all'applicazione di destinazione. È possibile specificare **/start** e **/attach** e le relative opzioni in un'unica riga di comando. È anche possibile aggiungere l'opzione **/globaloff** per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione. Usare quindi **/globalon** per iniziare a raccogliere i dati.  
  
#### <a name="to-attach-the-profiler-to-a-native-service"></a>Per connettere il profiler a un servizio nativo  
  
1.  Se il servizio non è in esecuzione, avviarlo.  
  
2.  Avviare il profiler digitando quanto segue al prompt dei comandi:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency   /output:** `OutputFile` [`Options`]  
  
    -   L'opzione [/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare qualsiasi opzione nella tabella seguente con l'opzione **/start**.  
  
    > [!NOTE]
    >  La maggior parte dei servizi richiede le opzioni **/user** e **/crosssession**.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName`|Specifica il dominio facoltativo e il nome utente dell'account a cui concedere l'accesso al profiler.|  
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni di accesso.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
3.  Connettere il profiler al servizio digitando il comando seguente al prompt dei comandi:  
  
     **VSPerfCmd /attach:** `PID`  
  
     `PID` specifica l'ID o il nome del processo dell'applicazione di destinazione. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file con le opzioni VSPerfCmd.exe. Per controllare la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le coppie di opzioni nella tabella seguente consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID di processo (`PID`) o dal nome di processo (*ProcName*). **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo.|  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, non deve essere in corso una raccolta di dati dal profiler. È possibile interrompere la raccolta dei dati da un servizio nativo profilato con il metodo di concorrenza interrompendo il servizio oppure richiamando l'opzione **VSPerfCmd /detach**. È quindi possibile richiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Disconnettere il profiler dall'applicazione di destinazione arrestando il servizio o digitando il comando seguente al prompt dei comandi:  
  
     Digitare **VSPerfCmd /detach**  
  
2.  Arrestare il profiler digitando il comando seguente al prompt dei comandi:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)