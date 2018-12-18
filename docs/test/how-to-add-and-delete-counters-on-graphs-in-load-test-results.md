---
title: Aggiungere ed eliminare contatori nei grafici nei risultati dei test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 1ec02769cc3960b4b1b7f4dd7a04d3d78193c1e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Procedura: aggiungere ed eliminare contatori nei grafici nei risultati dei test di carico

Per aggiungere contatori delle prestazioni a un grafico, è possibile utilizzare il riquadro Contatori.

 ![Contatore aggiunto a un grafico](../test/media/ltest_selectcounter.png "LTest_SelectCounter")

 **Considerazioni sull'intervallo di campionamento dei contatori delle prestazioni**

 Nelle impostazioni esecuzione test di carico scegliere un valore per la proprietà **Frequenza di campionamento** basato sulla lunghezza del test di carico. Una frequenza di campionamento inferiore, ad esempio il valore predefinito di cinque secondi, richiede più spazio nel database dei risultati del test di carico. Per i test di carico più lunghi, l'aumento della frequenza di campionamento riduce la quantità di dati raccolti. Per altre informazioni, vedere [Procedura: Specificare la frequenza di campionamento](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

 Di seguito sono riportate alcune linee guida per le frequenze di campionamento:

|Durata test di carico|Frequenza di campionamento consigliata|
|------------------------|-----------------------------|
|\< 1 ora|5 secondi|
|1 - 8 ore|15 secondi|
|8 - 24 ore|30 secondi|
|> 24 ore|60 secondi|

 **Considerazioni per l'inclusione di dettagli dell'intervallo per la raccolta di dati percentili**

 Nelle impostazioni esecuzione test dell'Editor test di carico è disponibile una proprietà denominata **Intervallo archiviazione dettagli**. Se la proprietà **Intervallo archiviazione dettagli** è abilitata, il tempo richiesto per eseguire ogni singolo test, transazione e pagina durante il test di carico verrà archiviato nel repository dei risultati del test di carico. Ciò consente di visualizzare i dati del novantesimo e del novantacinquesimo percentile nell'Analizzatore test di carico, nelle tabelle Test, Transazioni e Pagine.

 Per abilitare la proprietà **Intervallo archiviazione dettagli** nelle proprietà delle impostazioni esecuzione test sono disponibili due opzioni denominate **StatisticsOnly** e **AllIndividualDetails**. Con entrambe le opzioni viene determinato l'intervallo di tutti i singoli test, pagine e transazioni e dai singoli dati di intervallo vengono calcolati i dati percentili. La differenza per quanto riguarda l'opzione **StatisticsOnly** consiste nel fatto che i singoli dati di intervallo vengono eliminati dal repository dopo il calcolo dei dati percentili. In questo modo si riduce la quantità di spazio richiesta nel repository quando si usano i dettagli dell'intervallo. Gli utenti avanzati potrebbero tuttavia voler elaborare i dati dettaglio dell'intervallo in altri modi, usando strumenti SQL. In tal caso, è consigliabile usare l'opzione **AllIndividualDetails** in modo da rendere disponibili i dati dettaglio dell'intervallo per l'elaborazione. Se inoltre si imposta la proprietà su **AllIndividualDetails**, al termine dell'esecuzione del test di carico è possibile analizzare l'attività dell'utente virtuale usando Grafico attività utente virtuale nell'Analizzatore test di carico. Per altre informazioni, vedere [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

La quantità di spazio richiesta nel repository dei risultati del test di carico per l'archiviazione dei dati dettaglio dell'intervallo potrebbe essere molto elevata, soprattutto per i test di carico a esecuzione prolungata. Inoltre, è necessario più tempo per archiviare questi dati nel repository dei risultati alla fine del test di carico, in quanto tali dati vengono archiviati negli agenti del test di carico fino al termine dell'esecuzione del test di carico. Quando il test di carico viene completato, i dati vengono archiviati nel repository. La proprietà **Intervallo archiviazione dettagli** è abilitata per impostazione predefinita. Se ciò costituisce un problema per l'ambiente di test, è consigliabile impostare **Intervallo archiviazione dettagli** su **Nessuno**.

Per altre informazioni, vedere [Procedura: Specificare la proprietà Intervallo archiviazione dettagli](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Per visualizzare un determinato contatore delle prestazioni su un grafico del test di carico

1.  Dopo il completamento di un test di carico o dopo il caricamento del risultato di un test, scegliere **Grafici** nella barra degli strumenti dell'Analizzatore test di carico.

     Il pannello **Contatori** è visibile nella visualizzazione Grafici.

    > [!NOTE]
    > Se il pannello Contatori non è visibile, fare clic su **Mostra pannello dei contatori** nella barra degli strumenti.

2.  Nel riquadro Contatori espandere i nodi della gerarchia finché non si individua il contatore delle prestazioni da visualizzare graficamente.

     Ad esempio, per visualizzare la memoria disponibile in un computer in cui si stanno eseguendo i test, espandere **Computer**, espandere il nodo per il computer, quindi espandere **Memoria**. Verrà visualizzato il contatore **MB disponibili**.

3.  Selezionare il grafico del quale si desidera visualizzare il contatore delle prestazioni.

4.  Fare clic con il pulsante destro del mouse sul contatore delle prestazioni nel pannello **Contatori** e selezionare **Mostra contatore su grafico**.

    > [!TIP]
    > Per interrompere la visualizzazione dei dati del contatore delle prestazioni nel grafico, deselezionare la casella di controllo per il contatore delle prestazioni in Legenda. Ciò consente di visualizzare le statistiche relative a minimo, massimo e media senza visualizzare la linea di tendenza nel grafico. Ciò può rivelarsi utile se il grafico contiene le tracce di diversi contatori delle prestazioni sovrapposte durante l'analisi dei problemi. Per altre informazioni, vedere [Uso della legenda della visualizzazione Grafici per analizzare i test di carico](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5.  Per rimuovere dal grafico i dati relativi ai contatori delle prestazioni, fare clic con il pulsante destro del mouse sul contatore delle prestazioni nella colonna **Contatore** della legenda e selezionare **Elimina**.

     \- oppure -

     Fare clic con il pulsante destro del mouse sulla riga dei dati nel grafico e scegliere **Elimina**.

     \- oppure -

     Scegliere il contatore delle prestazioni nella colonna **Contatore** della legenda o sulla linea dei dati nel grafico, quindi premere il tasto **CANC**.

    > [!NOTE]
    > È inoltre possibile posizionare un contatore delle prestazioni sulla legenda, ma non sul grafico, mediante il comando **Mostra contatore su legenda**.

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md)