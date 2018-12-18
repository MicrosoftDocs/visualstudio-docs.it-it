---
title: Finestra di dialogo Impostazioni avanzate (visualizzatore di concorrenza) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0cde5d1ddd5dabfd42a6a7d31284736e24fa302
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Finestra di dialogo Impostazioni avanzate (visualizzatore di concorrenza)
La finestra **Impostazioni avanzate** del visualizzatore di concorrenza consente di controllare quali tracce vengono raccolte.  Nella finestra sono presenti le schede seguenti: Simboli, Just My Code, Buffer, Filtro, Eventi CLR, Marcatori, Provider e File.  
  
## <a name="symbols"></a>Simboli  
 Il visualizzatore di concorrenza usa le stesse impostazioni dei simboli del debugger di Visual Studio. Queste impostazioni vengono usate per risolvere gli stack di chiamate associati ai dati relativi alle prestazioni.  Quando elabora le tracce, il visualizzatore di concorrenza accede ai server di simboli specificati nella pagina delle impostazioni.  Quando si accede a questi dati in una rete, l'elaborazione delle tracce subisce un rallentamento.  Per ridurre il tempo necessario per risolvere simboli, è possibile memorizzarli nella cache in locale. Se i simboli sono stati scaricati, Visual Studio li caricherà dalla cache locale.  
  
## <a name="just-my-code"></a>Just My Code  
 Per impostazione predefinita, Just My Code è il set di file con estensione exe e dll associati alla soluzione corrente in Visual Studio. Il visualizzatore di concorrenza esamina questo set di file quando si usa la funzionalità Just My Code per filtrare gli stack di chiamate. Nella scheda Just My Code, è possibile aggiungere directory contenenti file con estensione exe e dll alle posizioni che il visualizzatore di concorrenza usa per Just My Code.  
  
 I percorsi dei file con estensione exe e dll vengono archiviati nel file di traccia quando la traccia viene raccolta.  La modifica di questa impostazione non ha alcun effetto sulle tracce raccolte in precedenza.  
  
## <a name="buffering"></a>Buffer  
 Per raccogliere una traccia, il visualizzatore di concorrenza usa ETW (Event Tracing for Windows).  Per l'archiviazione degli eventi, ETW usa diversi buffer.  Le impostazioni predefinite del buffer ETW possono non essere sempre ottimali e, in alcuni casi, possono causare problemi come la perdita di eventi.  Per configurare le impostazioni del buffer ETW, è possibile usare la scheda Buffer. Per altre informazioni, vedere [Registrazione di eventi](http://go.microsoft.com/fwlink/?LinkId=234579) e [EVENT_TRACE_PROPERTIES structure](http://go.microsoft.com/fwlink/?LinkId=234580) (Struttura EVENT_TRACE_PROPERTIES).  
  
## <a name="filter"></a>Filtro  
 Nella scheda Filtro è possibile selezionare il set di eventi raccolti dal visualizzatore di concorrenza. La selezione di un subset di eventi limita i tipi di dati visualizzati nei report, riduce la dimensione di ciascuna traccia e diminuisce il tempo necessario per l'elaborazione delle tracce.  
  
### <a name="clr-events"></a>Eventi CLR  
 Gli eventi generati da CLR (Common Language Runtime) consentono al visualizzatore di concorrenza di risolvere gli stack di chiamate gestite.  Se si disabilita la raccolta di eventi CLR, la dimensione della traccia risulta ridotta, ma alcuni stack di chiamate non verranno risolti.  Di conseguenza, alcune attività dei thread della CPU possono essere categorizzate in modo non corretto.  
  
### <a name="collect-for-native-processes"></a>Raccogli per processi nativi  
 Per impostazione predefinita, gli eventi CLR vengono raccolti solo quando un processo gestito viene profilato. Gli eventi CLR, infatti, non sono in genere necessari per i processi nativi.  In alcuni casi, ad esempio quando un processo nativo ospita il CLR, potrebbe essere necessario raccogliere eventi CLR per un processo nativo.  In questo caso, selezionare la casella di controllo **Raccogli per processi nativi**.  
  
### <a name="disable-rundown-events"></a>Disabilita eventi rundown  
 Il CLR genera gli eventi da due provider: runtime e rundown.  Se si vogliono raccogliere eventi CLR runtime, evitando però di raccogliere eventi rundown, selezionare la casella di controllo **Disabilita eventi rundown**.  Questa operazione riduce la dimensione del file di traccia generato dalla raccolta, ma è possibile che alcuni stack non vengano risolti. Per altre informazioni, vedere [CLR ETW Providers](/dotnet/framework/performance/clr-etw-providers) (Provider CLR ETW).  
  
### <a name="sample-events"></a>Eventi di esempio  
 È possibile usare eventi di esempio per raccogliere tutti gli stack di chiamate associati all'esecuzione di thread. Questi eventi vengono raccolti circa una volta ogni millisecondo nel processo corrente. Se la raccolta di eventi di esempio viene disabilitata, la dimensione della traccia raccolta risulta ridotta, ma non sarà possibile visualizzare alcuno stack di chiamate associato all'esecuzione del thread.  
  
### <a name="gpu-events"></a>Eventi GPU  
 Gli eventi GPU sono eventi generati da DirectX. Se la raccolta di eventi di GPU viene disabilitata, la dimensione della traccia raccolta risulta ridotta, ma non sarà possibile visualizzare alcuna attività GPU nella visualizzazione Utilizzo né alcuna attività del motore DirectX nella visualizzazione Thread.  
  
### <a name="file-io-events"></a>Eventi I/O su file  
 Gli eventi di I/O su file rappresentano gli accessi al disco per conto del processo corrente.  Se la raccolta di eventi di I/O su file viene disabilitata, la dimensione della traccia raccolta risulta ridotta, ma nella visualizzazione Thread non sarà riportata alcuna informazione sui canali o le operazioni del disco.  
  
## <a name="markers"></a>Marcatori  
 Nella scheda Marcatori è possibile configurare il set di provider ETW mostrati come marcatori nel visualizzatore di concorrenza.  È anche possibile filtrare la raccolta di marcatori in base al livello di importanza e alla categoria ETW.  Se si usa l'[SDK del visualizzatore di concorrenza ](../profiling/concurrency-visualizer-sdk.md) e il proprio provider marcatori, è possibile registrare qui quest'ultimo in modo che venga mostrato nella visualizzazione Thread.  
  
### <a name="adding-a-new-provider"></a>Aggiunta di un nuovo provider  
 Se il codice usa l'[SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md) o genera gli eventi ETW che seguono la convenzione <xref:System.Diagnostics.Tracing.EventSource>, è possibile visualizzare questi eventi nel visualizzatore di concorrenza registrandoli in questa finestra di dialogo.  
  
 Nel campo Nome immettere un nome che descrive i tipi di eventi generati dal provider.  Nel campo GUID immettere il GUID associato a questo provider. A ogni provider ETW è associato un GUID.  
  
 Facoltativamente, è possibile specificare se filtrare gli eventi da questo provider, in base alla categoria o al livello di importanza.  È possibile usare il campo categoria per applicare un filtro in base alle categorie dell'SDK del visualizzatore di concorrenza.  A questo scopo, immettere una stringa, delimitata da virgole, di categorie o di intervalli di categorie.  Con questa operazione vengono specificate le categorie di eventi del processo corrente da visualizzare.  Se si aggiunge un provider <xref:System.Diagnostics.Tracing.EventSource>, è possibile usare il campo relativo alla categoria per applicare un filtro in base alla parola chiave ETW.  Poiché la parola chiave è una maschera di bit, è possibile usare una stringa di interi, delimitata da virgole, per specificare i bit della maschera impostati. Ad esempio, "1,2" imposta il primo e il secondo bit e si traduce in 6 in formato decimale.  
  
 È possibile usare l'elenco dei livelli di importanza per filtrare gli eventi che hanno un'importanza o un livello ETW inferiore al valore specificato.  
  
### <a name="configuring-an-existing-provider"></a>Configurazione di un provider esistente  
 Per modificare le impostazioni associate a un provider esistente, selezionarlo dall'elenco e quindi scegliere il pulsante **Modifica provider**.  È possibile modificare le impostazioni relative al nome, al GUID e al filtro.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtrare i dati del marcatore all'esterno dei report del visualizzatore di concorrenza  
 Se non si vuole che i dati per un provider specifico vengano visualizzati in tracce future, deselezionare la casella di controllo accanto al provider da rimuovere.  
  
## <a name="files"></a>File  
 Nella scheda **File** è possibile specificare la directory in cui i file di traccia vengono archiviati ogni volta che una traccia viene raccolta.  Il visualizzatore di concorrenza genera quattro file per ogni traccia raccolta:  
  
-   File di log di traccia degli eventi (ETL) in modalità kernel (*.kernel.etl)  
  
-   File di log di traccia degli eventi in modalità utente (*.user.etl)  
  
-   File di dati del visualizzatore di concorrenza (*.CVData)  
  
-   File di traccia del visualizzatore di concorrenza (*.CVTrace)  
  
 Nei due file con estensione etl vengono archiviati i dati di traccia non elaborati, mentre nei due file del visualizzatore di concorrenza vengono archiviati i dati elaborati.  I file con estensione etl non elaborati non vengono usati dopo l'elaborazione di una traccia.  La selezione della casella di controllo **Elimina i file di log traccia eventi (ETL) dopo l'analisi** riduce la quantità di dati di traccia archiviati nel disco.  
  
## <a name="see-also"></a>Vedere anche  
 [Just My Code](../profiling/just-my-code-threads-view.md)   
 [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)