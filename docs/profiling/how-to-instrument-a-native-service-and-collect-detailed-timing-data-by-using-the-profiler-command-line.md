---
title: 'Procedura: Instrumentare un servizio nativo e raccogliere dati di intervallo dettagliati tramite la riga di comando del profiler | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9dcd4052078a3a7327b0a48fca8812a2d5393917
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Procedura: instrumentare un servizio nativo e raccogliere dati di intervallo dettagliati tramite la riga di comando del profiler
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un servizio (C/C++) nativo e raccogliere dati di intervallo dettagliati.  
  
> [!NOTE]
>  Non è possibile profilare un servizio con il metodo di strumentazione se il servizio non può essere riavviato dopo l'avvio del computer, ad esempio un servizio che viene avviato solo all'avvio del sistema operativo.  
>   
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere dati di intervallo dettagliati da un servizio nativo usando il metodo di strumentazione, usare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente. Sostituire quindi la versione non instrumentata del servizio con la versione instrumentata, assicurandosi che il servizio sia configurato per l'avvio manuale. Avviare quindi il profiler.  
  
 Quando viene avviato il servizio, i dati di intervallo vengono raccolti automaticamente in un file di dati. È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilatura.  
  
 Per terminare una sessione di profilatura, chiudere il servizio e arrestare in modo esplicito il profiler.  
  
## <a name="starting-the-application-with-the-profiler"></a>Avvio dell'applicazione con il profiler  
  
#### <a name="to-start-profiling-a-native-service"></a>Per avviare la profilatura di un servizio nativo  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Usare lo strumento **VSInstr** per generare una versione instrumentata del file binario del servizio.  
  
3.  Sostituire il file binario originale con la versione instrumentata. In Gestione controllo servizi di Windows assicurarsi che tipo di avvio del servizio sia impostato su Manuale.  
  
4.  Avvia il profiler. Tipo:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   L'opzione **/start:trace** inizializza il profiler.  
  
    -   L'opzione **/output:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:trace**.  
  
    > [!NOTE]
    >  Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni di accesso. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'ID di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**.|  
    |[/waitstart](../profiling/waitstart.md)[**:**`Interval`]|Specifica il numero di secondi di attesa dell'inizializzazione del profiler prima che venga restituito un errore. Se `Interval` non viene specificato, il profiler attende per un tempo indefinito. Per impostazione predefinita, **/start** restituisce immediatamente un valore.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **/globaloff** alla riga di comando **/start**. Usare **/globalon** per riprendere la profilatura.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Raccoglie informazioni dal contatore delle prestazioni del processore specificato in Config. Le informazioni del contatore vengono aggiunte ai dati raccolti a ogni evento di profilatura.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
5.  Avviare il servizio da Gestione controllo servizi.  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Mentre il servizio è in esecuzione, è possibile usare le opzioni di **VSPerfCmd.exe** per avviare e arrestare la scrittura dei dati nel file di dati del profiler. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto del servizio.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le seguenti coppie di opzioni **VSPerfCmd** consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, arrestare il servizio che esegue il componente instrumentato e quindi chiamare l'opzione **VSPerfCmd**[/shutdown](../profiling/shutdown.md) per disabilitare il profiler e chiudere il file dei dati di profilatura.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Arrestare il servizio da Gestione controllo servizi.  
  
2.  Arrestare il profiler. Tipo:  
  
     **VSPerfCmd /shutdown**  
  
3.  Sostituire il modulo instrumentato con l'originale. Se necessario, riconfigurare il tipo di avvio del servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)   
 [Instrumentation Method Data Views](../profiling/instrumentation-method-data-views.md) (Visualizzazioni dei dati del metodo di strumentazione)