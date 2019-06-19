---
title: Collegare il profiler a un servizio .NET per raccogliere dati sulla concorrenza
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9b77d4e27edd470d83941e29d5d7a2314cd2a8e1
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746261"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Procedura: Connettere il profiler a un servizio .NET per raccogliere dati di concorrenza tramite la riga di comando
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un servizio .NET Framework e raccogliere dati di concorrenza di thread e processi tramite il metodo di campionamento.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Per raccogliere i dati di concorrenza, connettere il profiler al processo del servizio. Quando il profiler è connesso al servizio, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura, il profiler non deve essere più connesso al servizio e deve essere arrestato in modo esplicito. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="attach-the-profiler"></a>Connettere il profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Per connettere il profiler a un servizio .NET Framework

1. Installare il servizio.

2. Aprire una finestra dei comandi.

3. Inizializzare le variabili di ambiente di profilatura. Tipo:

     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [ **/samplelineoff**]

    - **/globalsampleon** abilita il campionamento.

    - **/samplelineoff** disabilita l'assegnazione dei dati raccolti a righe specifiche del codice sorgente. Quando viene specificata questa opzione, i dati vengono assegnati solo alle funzioni.

4. Riavviare il computer.

5. Avvia il profiler. Tipo:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     L'opzione [/output](../profiling/output.md) **:** `OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start**.

    > [!NOTE]
    > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per i servizi.

    |Opzione|Description|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna **Nome utente** nella scheda **Processi** di Gestione attività di Windows.|
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se il servizio è in esecuzione in una sessione diversa. L'ID di sessione è elencato nella colonna **ID sessione** della scheda **Processi** di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*.|

6. Se necessario, avviare il servizio.

7. Connettere il profiler al servizio. Tipo:

     **VSPerfCmd /attach:** `PID` [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID` specifica l'ID o il nome del processo del servizio. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.

    - **targetclr:** `Version` specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione. Facoltativo.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre è in esecuzione il servizio, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le seguenti coppie di opzioni **VSPerfCmd** consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia ( **/globalon**) o interrompe ( **/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia ( **/processon**) o interrompe ( **/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID o dal nome di processo. **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|

- È anche possibile usare l'opzione **VSPerfCmd.exe**[/mark](../profiling/mark.md) per inserire un indicatore di profilatura nel file di dati. Il comando **/mark** aggiunge un identificatore, un timestamp e una stringa di testo facoltativa definita dall'utente. Gli indicatori possono essere usati per filtrare i dati nei rapporti e nelle visualizzazioni dei dati del profiler. Le seguenti coppie di opzioni VSPerfCmd consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, non deve essere in corso una raccolta di dati dal profiler. È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di concorrenza interrompendo il servizio oppure richiamando l'opzione **VSPerfCmd /detach**. È quindi possibile richiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura, ma la configurazione di sistema non viene reimpostata fino al riavvio del computer.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione.

    - Arrestare il servizio.

         -oppure-

    - Digitare **VSPerfCmd /detach**.

2. Arrestare il profiler. Tipo:

     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)
