---
title: La diagnosi di estensione dell'interfaccia utente Ritarda in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 01/26/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: b63f9538c916b74874031704a1f60d0646f8d032
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Procedura: diagnosticare UI ritardi causati dalle estensioni

Quando l'interfaccia utente non risponde, Visual Studio esamina lo stack di chiamate del thread dell'interfaccia utente, a partire da foglia e procedendo verso la base. Se Visual Studio determina che un frame sullo stack di chiamate appartiene a un modulo che fa parte di un'estensione installata e abilitata, verrà visualizzata una notifica.

![Ritardo dell'interfaccia utente (il blocco) notifica](media/ui-delay-notification-in-vs.png)

La notifica informa l'utente che il ritardo dell'interfaccia utente (ad esempio il problema del blocco nell'interfaccia utente) potrebbe essere stato il risultato del codice di un'estensione. Fornisce inoltre l'utente con le opzioni per disabilitare l'estensione o notifiche in futuro per l'estensione.

Questo documento descrive come eseguire la diagnostica nel codice dell'estensione cause delle notifiche di ritardo dell'interfaccia utente. 

> [!NOTE]
> Non utilizzare l'istanza sperimentale di Visual Studio per diagnosticare i ritardi dell'interfaccia utente. Quando si utilizza l'istanza sperimentale, vale a dire che le notifiche di ritardo dell'interfaccia utente potrebbero non essere visualizzate, alcune parti dell'analisi dello stack di chiamata necessaria per le notifiche di ritardo dell'interfaccia utente sono disattivate.

Una panoramica del processo di diagnostica è come segue:
1. Identificare lo scenario di trigger.
2. Riavviare VS con attività di accesso.
3. Avviare l'analisi ETW.
4. Attivare la notifica verrà nuovamente visualizzato.
5. Arrestare l'analisi ETW.
6. Esaminare il registro attività per ottenere l'ID di ritardo.
7. Analizzare la traccia ETW usando un ID di ritardo del passaggio 6.

Nelle sezioni seguenti verranno esaminate con la procedura in modo più dettagliato.

## <a name="identifying-the-trigger-scenario"></a>Che identifica lo scenario di trigger

Per diagnosticare un ritardo dell'interfaccia utente, è necessario innanzitutto identificare quali (sequenza di azioni) fa sì che Visual Studio per visualizzare la notifica. Si tratta affinché sia in grado di attivare la notifica in un secondo momento con la registrazione attivata.

## <a name="restarting-vs-with-activity-logging-on"></a>Il riavvio di VS con attività di accesso

Visual Studio è possibile generare un log"attività" che fornisce informazioni utili durante il debug di un problema. Per attivare la registrazione in Visual Studio delle attività, avviare Visual Studio con il `/log` opzione della riga di comando. Dopo l'avvio di Visual Studio, il log di attività viene archiviato nel percorso seguente:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Per ulteriori informazioni su come è possibile trovare il VS ID istanza, vedere [strumenti per il rilevamento e la gestione di istanze di Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Si utilizzerà questo log attività in un secondo momento per scoprire ulteriori informazioni su ritardi dell'interfaccia utente e le notifiche correlate.

## <a name="starting-etw-tracing"></a>Avviare l'analisi ETW

È possibile utilizzare [PerfView](https://github.com/Microsoft/perfview/) per raccogliere una traccia ETW. PerfView fornisce un'interfaccia di facile utilizzo per la raccolta di una traccia ETW e per eseguire l'analisi. Per raccogliere una traccia, utilizzare il comando seguente:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

In questo modo il provider "Microsoft VisualStudio", ovvero il provider di che Visual Studio utilizza per gli eventi correlati alle notifiche di ritardo dell'interfaccia utente. Specifica inoltre la parola chiave per il provider del kernel che PerfView è possibile utilizzare per generare la vista "Thread ora stack".

## <a name="triggering-the-notification-to-appear-again"></a>Per visualizzare nuovamente la notifica di attivazione

Una volta avviata la raccolta di traccia PerfView, è possibile utilizzare la sequenza di azioni di trigger (dal passaggio 1) per la notifica verrà nuovamente visualizzato. Quando viene visualizzata la notifica, è possibile interrompere la raccolta di traccia per PerfView elaborare e generare il file di output di traccia.

## <a name="stopping-etw-tracing"></a>L'arresto di traccia ETW

Per interrompere la raccolta di traccia, è sufficiente utilizzare il `Stop collection` pulsante nella finestra di PerfView. Dopo aver interrotto la raccolta di traccia, PerfView elaborerà automaticamente gli eventi ETW e genera un file di output di traccia.

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>Esaminare il registro attività per ottenere l'ID di ritardo

Come accennato in precedenza, è possibile trovare il log attività `%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`. Ogni volta che Visual Studio rileva una ritardo dell'interfaccia utente di estensione, viene scritto un nodo nel log di attività con `UIDelayNotifications` come origine. Questo nodo contiene quattro tipi di informazioni del ritardo dell'interfaccia utente:

- L'ID del ritardo dell'interfaccia utente, un numero sequenziale che identifica in modo univoco un ritardo dell'interfaccia utente in una sessione di Visual Studio
- L'ID di sessione, che identifica in modo univoco la sessione di Visual Studio dall'inizio alla chiusura
- Visualizzato o meno una notifica per il ritardo dell'interfaccia utente
- L'estensione per il ritardo dell'interfaccia utente più probabile

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Non tutti i risultati di ritardi dell'interfaccia utente in una notifica. Pertanto, verificare sempre la "notifica illustrata?" valore per identificare correttamente il ritardo dell'interfaccia utente di destra.

Dopo aver trovato il ritardo dell'interfaccia utente corretto nel registro attività, annotare l'ID di ritardo dell'interfaccia utente specificato nel nodo. Utilizzare l'ID per cercare l'evento ETW corrispondente nel passaggio successivo.

## <a name="analyzing-the-etw-trace"></a>L'analisi di traccia ETW

Successivamente, aprire il file di traccia. È possibile farlo usando la stessa istanza di PerfView o avviando una nuova istanza e impostando il percorso della cartella corrente nella parte superiore sinistra della finestra per il percorso del file di traccia.

![Impostare il percorso della cartella in Perfview](media/perfview-set-path.png)

Quindi, selezionare il file di traccia nel riquadro a sinistra e aprirlo scegliendo Apri dal menu di scelta o contesto.

> [!NOTE]
> Per impostazione predefinita PerfView genera un archivio Zip. Quando si apre trace.zip, automaticamente decomprime l'archivio e verrà visualizzata la traccia. È possibile ignorare questo passaggio deselezionando la casella "Zip" durante la raccolta di traccia. Tuttavia, se si intende trasferire e utilizzare le tracce in computer diversi, è consigliabile evitare deselezionando la casella "Zip". Senza questa opzione, i PDB obbligatori per gli assembly Ngen di accompagnamento non la traccia e pertanto i simboli da assembly Ngen non verranno risolti in computer di destinazione. (Vedere [questo post di blog](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) per ulteriori informazioni sui file PDB per gli assembly Ngen.) 

Può richiedere diversi minuti prima che PerfView elaborare e aprire la traccia. Dopo avere aperta la traccia, viene visualizzato un elenco di vari "visualizzazioni" in essa contenute.

![Visualizzazione di riepilogo di PerfView traccia](media/perfview-summary-view-events-selected.png)

Si utilizzerà innanzitutto la vista "Eventi" per ottenere l'intervallo di tempo del ritardo dell'interfaccia utente:

1. Aprire la vista "Eventi" selezionando il nodo di "Eventi" in una traccia e scegliendo Apri dal menu di scelta o contesto.
2. Selezionare "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" nel riquadro a sinistra.
3. Premere INVIO

La selezione viene applicata e tutte le `ExtensionUIUnresponsiveness` gli eventi vengono visualizzati nel riquadro di destra.

![Selezione degli eventi nella visualizzazione eventi](media/perfview-event-selection.png)

Ogni riga nel riquadro di destra corrisponde a un ritardo dell'interfaccia utente. L'evento include un valore di "Ritardo ID" che deve corrispondere all'ID di ritardo nel log attività nel passaggio 6. Poiché `ExtensionUIUnresponsiveness` viene generato alla fine del ritardo dell'interfaccia utente, il timestamp dell'evento (approssimativamente) segni l'ora di fine del ritardo dell'interfaccia utente. L'evento contiene anche la durata del ritardo. È possibile sottrarre la durata tra il timestamp di fine per ottenere il timestamp dell'avvio il ritardo dell'interfaccia utente.

![Calcolare l'intervallo di tempo di ritardo dell'interfaccia utente](media/ui-delay-time-range.png)

Nella schermata precedente, ad esempio, il timestamp dell'evento è 12,125.679 e la durata del ritardo è 6,143.085 (ms). Pertanto
* L'inizio di ritardo è 12,125.679 6,143.085 = 5,982.594.
* L'intervallo di tempo di ritardo dell'interfaccia utente è 5,982.594 a 12,125.679.

Una volta che l'intervallo di tempo, è possibile chiudere la vista degli eventi e aprire la visualizzazione "Stack di Thread di esecuzione (con le attività StartStop)". Questa visualizzazione è particolarmente utile in quanto spesso le estensioni che bloccano il thread dell'interfaccia utente sono semplicemente in attesa di un'operazione O associate ai / o di altri thread. Di conseguenza, la vista "CPU Stack", che è l'opzione come per la maggior parte dei casi, non può acquisire il thread di tempi di blocco in quanto non viene usato questo periodo di tempo della CPU. Gli "Thread ora stack" risolve questo problema, correttamente con bloccato ora.

![Nodo di stack di esecuzione (con le attività StartStop) di thread nella visualizzazione Riepilogo PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Durante l'apertura "Thread stack in fase di" consente di visualizzare, scegliere il processo "devenv" per avviare l'analisi.

![Visualizza gli stack di tempo per l'analisi di ritardo dell'interfaccia utente del thread](media/ui-delay-thread-time-stacks.png)

Nella vista "Thread ora stack", in alto a sinistra della pagina, è possibile impostare l'intervallo di tempo per i valori che è calcolati nel passaggio precedente e premere INVIO, quindi gli stack vengono adattati per l'intervallo di tempo.

> [!NOTE]
> Determinare il thread è l'interfaccia utente di thread (avvio) può essere poco intuitivi traccia raccolta se è stata avviata dopo Visual Studio è già aperto. Tuttavia, i primi elementi nello stack del thread dell'interfaccia utente (avvio) sono più probabile sempre DLL del sistema operativo (ntdll.dll e kernel32.dll) seguita da devenv!? e quindi msenv!?. Questa sequenza consente di identificare il thread dell'interfaccia utente.

 ![Che identifica il thread di avvio](media/ui-delay-startup-thread.png)

È inoltre possibile filtrare ulteriormente questa vista includendo solo gli stack che contengono moduli dal pacchetto.

* Impostare "GroupPats" testo vuoto per rimuovere qualsiasi raggruppamento aggiunto per impostazione predefinita.
* Set "IncPats" per includere una parte del nome dell'assembly, oltre a filtro di processo esistente. In questo caso, deve essere "devenv; UIDelayR2 ".

![Impostazione GroupPath e IncPath in visualizzazione finestra Stack in fase di Thread](media/perfview-tts-group-path-inc-path.png)

PerfView è dettagliate informazioni aggiuntive nel menu della Guida che è possibile utilizzare per identificare eventuali colli di bottiglia nel codice. Inoltre, i collegamenti seguenti forniscono ulteriori informazioni su come utilizzare le API per ottimizzare il codice di threading di Visual Studio:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

È inoltre possibile utilizzare gli analizzatori statici nuova di Visual Studio per le estensioni (pacchetto NuGet [qui](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), che forniscono informazioni aggiuntive sulle procedure consigliate per la scrittura di estensioni efficiente. Visualizzare un elenco di [gli analizzatori di VS SDK](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) e [threading analizzatori](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Se non si riesce a risolvere il problema del blocco a causa di dipendenze non abbia il controllo (ad esempio, se l'estensione deve chiamare servizi VS sincrona nel thread UI), si desidera riportarlo. Se si è un membro del programma per i Partner di Visual Studio, è possibile contattarci inviando una richiesta di supporto per sviluppatori. In caso contrario, utilizzare lo strumento 'Segnala un problema' per inviare commenti e suggerimenti e includere `"Extension UI Delay Notifications"` nel titolo. Includere inoltre una descrizione dettagliata dell'analisi.
