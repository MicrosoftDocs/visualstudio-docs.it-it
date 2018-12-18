---
title: Pannello dei contatori per l'analisi dei test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counters panel
ms.assetid: e1a388d7-5d33-4631-931a-5653ac4aefdc
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: f6543cc42d6ac62a252b450a232700b17f05b719
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-counters-panel-in-graphs-view-and-tables-view"></a>Usare il pannello dei contatori nella visualizzazione Grafici e nella visualizzazione Tabelle

Il pannello Contatori è visibile nella visualizzazione Grafici e nella visualizzazione Tabelle nell'analizzatore test di carico mentre è in esecuzione un test di carico o quando si analizza un risultato del test di carico. Per altre informazioni, vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md), [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) e [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md).

Nel riquadro Contatori è fornita una visualizzazione strutturata di tutti i contatori delle prestazioni che sono stati raccolti durante il test di carico. È possibile visualizzare o nascondere il pannello dei contatori scegliendo **Mostra pannello dei contatori** nella barra degli strumenti dell'analizzatore test di carico.

I contatori sono organizzati in una struttura ad albero, in cui i nodi foglia corrispondono alle istanze dei contatori delle prestazioni che possono essere rappresentate in un grafico.

Nel riquadro Contatori sono disponibili le seguenti funzionalità:

-   Comunicazione delle informazioni sulle violazioni di soglia.

-   Selezione di contatori per la creazione di grafici.

-   Visualizzazione albero di tutti i contatori delle prestazioni raccolti durante l'esecuzione di un test di carico, con i seguenti rami principali:

    -   **Globale:** contiene i dati di riepilogo dei contatori delle prestazioni per ogni agente di test e per l'intero test di carico.

    -   **Nome scenario:** nella struttura ad albero del contatore delle prestazioni i rami identificati con nomi di scenario di test di carico contengono tutte le istanze dei contatori dei test di carico associate a un particolare scenario di test. La maggior parte dei contatori di test di carico sono annidati all'interno di un ramo di scenario.

         Un ramo di scenario contiene nodi di test delle prestazioni Web. I nodi di test delle prestazioni Web contengono i nodi Pagine, Richieste e Transazioni. Ogni nodo foglia in questa struttura corrisponde a un contatore delle prestazioni che può essere aggiunto a un grafico.

    -   **Computer:** contiene tutte le istanze di contatori non destinati ai test di carico, raggruppate per computer. Il ramo Computer contiene un nodo per ogni computer associato al controller del test di carico specificato nella sezione Ruoli delle impostazioni di test attualmente selezionate. Per altre informazioni, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

         Ogni nodo del computer contiene un set di categorie di contatori delle prestazioni raccolto da quel computer. Le categorie contengono contatori e i contatori contengono nomi di istanza dei contatori delle prestazioni.

    -   **Errori:** contiene tutti gli errori rilevati durante il test di carico. Il nodo Errori contiene diversi nodi di errori di sottocategorie. Le sottocategorie sono specifiche per diversi tipi di errori, ad esempio, le eccezioni e gli errori HTTP.

### <a name="scenario-name-node-in-counters-panel"></a>Nodo Nome scenario nel pannello Contatori

|||
|-|-|
|![Nodo con nome dello scenario di riquadro dei contatori](../test/media/ltest__namenode.png)|1. Tutti i contatori delle prestazioni associati a Scenario1 del test di carico vengono visualizzati sotto questo nodo.<br />2. Tutti i test relativi a uno scenario si trovano sotto il nodo dello scenario. L'etichetta indica il nome del test.<br />3. I nodi foglia sotto un nodo del test corrispondono a contatori di test case per test di carico, dove il nome dell'istanza del contatore corrisponde al nome del test.<br />4. Tutte le istanze del contatore di pagine del test di carico associate a un ramo del test delle prestazioni Web. In questo nodo sono contenute tutte le istanze del contatore di pagine del test di carico associate a Login GET (nome del rapporto) del test delle prestazioni Web IBuyBrowse in Scenario1 del test di carico.<br />5. I nodi foglia sotto un nodo pagina sono contatori di pagine del test di carico.<br />6. Tutte le istanze del contatore di richieste del test di carico associate a un test delle prestazioni Web sono contenute all'interno di un ramo di test delle prestazioni Web. In questo nodo sono contenute tutte le istanze del contatore di richieste associate alla richiesta Login GET (nome del rapporto) del test delle prestazioni Web IBuyBrowse in Scenario1 del test di carico.<br />7. I nodi foglia sotto un nodo richiesta sono contatori di richieste del test di carico.<br />8. Tutte le istanze del contatore di transazioni del test di carico associate a un test delle prestazioni Web sono contenute all'interno di un ramo di test delle prestazioni Web. In questo nodo sono contenute tutte le istanze del contatore di transazioni associate alla transazione denominata Transaction1 del test delle prestazioni Web IBuyBrowse in Scenario1 del test di carico.<br />9. I nodi foglia sotto un nodo transazione sono contatori di transazioni del test di carico.<br />10. Nodo unit test.|

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Aggiungere più contatori delle prestazioni a un grafico nella visualizzazione grafico:** nel pannello dei contatori è possibile aggiungere diversi tipi di dati a un grafico del test di carico aggiungendo più contatori delle prestazioni nel grafico.|-   [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Analizzare tutte le soglie specificate nel test di carico violate:** nel pannello dei contatori vengono visualizzate le icone che rappresentano le violazioni di soglia che è possibile aggiungere a tabelle e grafici per un'ulteriore analisi.|-   [Procedura: Analizzare le violazioni di soglia usando il pannello dei contatori](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|**Analizzare tutti gli errori rilevati durante l'esecuzione del test di carico:** nel pannello dei contatori è incluso un nodo degli errori che contiene le categorie e le sottocategorie di errore, ad esempio gli errori HTTP, che è possibile usare per aggiungere gli errori ai grafici per un'ulteriore analisi.|-   [Procedura: Analizzare gli errori usando il pannello dei contatori](../test/how-to-analyze-errors-using-the-counters-panel.md)|

## <a name="performance-counter-sampling-interval-considerations"></a>Considerazioni sull'intervallo di campionamento dei contatori delle prestazioni

Nelle impostazioni esecuzione test di carico scegliere un valore per la proprietà **Frequenza di campionamento** basato sulla lunghezza del test di carico. Una frequenza di campionamento inferiore, ad esempio il valore predefinito di cinque secondi, richiede più spazio nel database dei risultati del test di carico. Per i test di carico più lunghi, l'aumento della frequenza di campionamento riduce la quantità di dati raccolti. Per altre informazioni, vedere [Procedura: Specificare la frequenza di campionamento](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Di seguito sono riportate alcune linee guida per le frequenze di campionamento:

|Durata test di carico|Frequenza di campionamento consigliata|
|------------------------|-----------------------------|
|\< 1 ora|5 secondi|
|1 - 8 ore|15 secondi|
|8 - 24 ore|30 secondi|
|> 24 ore|60 secondi|

## <a name="considerations-for-including-timing-details-to-collect-percentile-data"></a>Considerazioni per l'inclusione di dettagli dell'intervallo per la raccolta di dati percentili

Nelle impostazioni esecuzione test dell'Editor test di carico è disponibile una proprietà denominata **Intervallo archiviazione dettagli**. Se la proprietà **Intervallo archiviazione dettagli** è abilitata, il tempo richiesto per eseguire separatamente ogni test, transazione e pagina durante il test di carico verrà archiviato nel repository dei risultati del test di carico. Ciò consente di visualizzare i dati del novantesimo e del novantacinquesimo percentile nell'Analizzatore test di carico, nelle tabelle Test, Transazioni e Pagine.

Per abilitare la proprietà **Intervallo archiviazione dettagli** nelle proprietà delle impostazioni di esecuzione test sono disponibili due opzioni: **StatisticsOnly** e **AllIndividualDetails**. Con entrambe le opzioni viene determinato l'intervallo di tutti i singoli test, pagine e transazioni e dai singoli dati di intervallo vengono calcolati i dati percentili. La differenza per quanto riguarda l'opzione **StatisticsOnly** consiste nel fatto che i singoli dati di intervallo vengono eliminati dal repository dopo il calcolo dei dati percentili. In questo modo si riduce la quantità di spazio richiesta nel repository quando si usano i dettagli dell'intervallo. Gli utenti avanzati potrebbero tuttavia voler elaborare i dati dettaglio dell'intervallo in altri modi, usando strumenti SQL. In tal caso, è consigliabile usare l'opzione **AllIndividualDetails** in modo da rendere disponibili i dati dettaglio dell'intervallo per l'elaborazione. Se inoltre si imposta la proprietà su **AllIndividualDetails**, al termine dell'esecuzione del test di carico sarà possibile analizzare l'attività dell'utente virtuale usando il Grafico attività utente virtuale nell'analizzatore test di carico. Per altre informazioni, vedere [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

La quantità di spazio necessaria nel repository dei risultati del test di carico per l'archiviazione dei dati dettaglio dell'intervallo potrebbe essere elevata, soprattutto per i test di carico a esecuzione prolungata. Inoltre, è necessario più tempo per archiviare questi dati nel repository dei risultati alla fine del test di carico, in quanto tali dati vengono archiviati negli agenti del test di carico fino al termine dell'esecuzione del test di carico. Quando il test di carico viene completato, i dati vengono archiviati nel repository. La proprietà **Intervallo archiviazione dettagli** è abilitata per impostazione predefinita. Se ciò costituisce un problema per l'ambiente di test, è consigliabile impostare **Intervallo archiviazione dettagli** su **Nessuno**.

Per altre informazioni, vedere [Procedura: Specificare la proprietà Intervallo archiviazione dettagli](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)