---
title: Panoramica sul riepilogo dei risultati dei test di carico | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 001f7f866437807565bc83a8ad3a4dd809dd4100
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="load-test-results-summary-overview"></a>Cenni preliminari sul riepilogo dei risultati dei test di carico

Una volta terminata l'esecuzione, è possibile visualizzare il riepilogo dei test di carico per verificarne rapidamente i risultati. Nel riepilogo dei test di carico sono riportati i risultati principali in un formato compatto e di agevole lettura. Il riepilogo può anche essere stampato per comunicare più agevolmente i risultati dei test di carico agli stakeholder. Il riepilogo del test di carico è inoltre alla visualizzazione predefinita quando si apre un risultato del test di carico da un test di carico eseguito precedentemente. Per altre informazioni, vedere [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md).

 ![Visualizzazione Riepilogo](../test/media/ltest_summaryview.png "LTest_SummaryView")

## <a name="the-load-test-summary"></a>Riepilogo del test di carico

Il riepilogo del test di carico è suddiviso in sezioni. Le sezioni iniziali sono riportate all'inizio del riepilogo e sono sempre visibili. Quando si visualizza il riepilogo del test di carico, i primi elementi sono i seguenti:

- Informazioni sull'esecuzione di test

- Risultati complessivi

- Statistica: le prime 5 pagine più lente

- Statistica: i primi 5 test più lenti

- Statistica: le prime 5 operazioni SQL più lente

    > [!NOTE]
    > La sezione relativa alle operazioni SQL è visualizzata solo se la traccia SQL è attivata nel test di carico.

Le ultime sezioni sono riportate alla fine del riepilogo e possono essere compresse per ridurre le dimensioni del riepilogo. Tali sezioni sono le seguenti:

- Risultati del test

- Risultati pagina

- Risultati transazione

- Risorse sistema sotto test

- Risorse controller e agenti

- Errori

## <a name="test-run-information"></a>Informazioni sull'esecuzione di test

La sezione relativa alle informazioni sull'esecuzione del test contiene informazioni generali sull'esecuzione quali il nome del test, l'ora di inizio e l'ora di fine e il controller che ha eseguito il test. Inoltre, è compresa l'eventuale descrizione facoltativa aggiunta all'esecuzione del test di carico.

## <a name="overall-results"></a>Risultati complessivi

La sezione relativa ai risultati complessivi contiene i risultati di riepilogo del test incluso il numero di richieste per secondo, il numero totale delle richieste non riuscite, il tempo medio di risposta e il tempo medio di pagina.

## <a name="key-statistic-top-5-slowest-pages"></a>Statistica: le prime 5 pagine più lente

La sezione contiene informazioni sulle prime cinque pagine più lente del test di carico. Per ogni pagina sono visualizzati l'URL e il tempo medio di caricamento. Le pagine sono elencate in ordine decrescente. È possibile scegliere l'URL di una pagina per aprire la tabella **Pagine** ed esaminare altri dettagli sulla pagina. Per altre informazioni, vedere [Procedura: Visualizzare la risposta delle pagine Web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Il valore percentile per il rapporto **Tempo pagina 95% (sec)** indica che il 95% delle pagine è stato completato in meno di questo intervallo in secondi.

## <a name="key-statistic-top-5-slowest-tests"></a>Statistica: i primi 5 test più lenti

La sezione contiene informazioni sui primi cinque test più lenti del test di carico. Per ogni test sono visualizzati il nome e il tempo medio di esecuzione. I test sono elencati in ordine decrescente. È possibile scegliere il nome di un test per aprire la tabella **Test** ed esaminare altri dettagli sul test. Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Il valore percentile per il rapporto **Tempo test 95% (sec)** indica che il 95% dei test è stato completato in meno di questo intervallo in secondi.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Statistica: le prime 5 operazioni SQL più lente

Se la traccia SQL è attivata nel test di carico, questa sezione contiene informazioni sulle 5 query più lente del test di carico. Per ogni operazione sono visualizzati il nome e la durata espressa in microsecondi (SQL Server 2005) o in millisecondi (SQL Server 2000 e versioni precedenti). I test sono elencati in ordine decrescente in base alla durata. È possibile scegliere il nome di un'operazione per aprire la tabella **Traccia SQL** ed esaminare altri dettagli sull'operazione. Per altre informazioni, vedere la [tabella dei dati di Traccia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Risultati del test

La sezione relativa ai risultati del test contiene un elenco di tutti i test e degli scenari del test di carico. Per ogni test sono visualizzati il nome, lo scenario, il numero di esecuzioni, il numero di volte che non è stato superato e il tempo medio. È possibile scegliere il nome di un test per aprire la tabella **Test** ed esaminare altri dettagli sul test. Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> È possibile comprimere ed espandere questa sezione scegliendo la freccia alla sinistra del titolo della sezione.

## <a name="page-results"></a>Risultati della pagina

La sezione relativa ai risultati di pagina contiene un elenco di tutte le pagine Web del test di carico. Sono visualizzati l'URL, lo scenario, il nome del test, il tempo medio e il conteggio delle pagine. È possibile scegliere l'URL di una pagina per aprire la tabella **Pagine** ed esaminare altri dettagli sulla pagina. Per altre informazioni, vedere [Procedura: Visualizzare la risposta delle pagine Web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> È possibile comprimere ed espandere questa sezione scegliendo la freccia alla sinistra del titolo della sezione.

## <a name="transaction-results"></a>Risultati della transazione

La sezione relativa ai risultati di transazione contiene un elenco di tutte le transazioni del test di carico. Sono visualizzati il nome, lo scenario, il test, il tempo di risposta, il tempo trascorso e il conteggio delle transazioni. È possibile scegliere il nome di una transazione per aprire la tabella **Transazioni** ed esaminare altri dettagli sulla transazione. Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> È possibile comprimere ed espandere questa sezione scegliendo la freccia alla sinistra del titolo della sezione.

I valori percentili indicano le seguenti informazioni sulla transazione:

-   Il 90% delle transazioni totali è stato completato in meno di \<numero> secondi.

-   Il 95% delle transazioni totali è stato completato in meno di \<numero> secondi.

## <a name="system-under-test-resources"></a>Risorse sistema sotto test

La sezione relativa alle risorse di sistema sotto test contiene un elenco dei computer che costituiscono l'insieme dei computer di destinazione per cui è stato generato il carico. Include tutti i computer da cui vengono raccolti gli insiemi di contatori diversi da agenti o controller. Sono visualizzati il nome del computer, il tempo processore in percentuale e la memoria disponibile. È possibile scegliere il nome di un computer per aprire il grafico **Sistema sottoposto a test** e verificare l'uso delle risorse nel tempo. Per altre informazioni, vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> È possibile comprimere ed espandere questa sezione scegliendo la freccia alla sinistra del titolo della sezione.

## <a name="controller-and-agent-resources"></a>Risorse controller e agenti

La sezione relativa alle risorse controller e agenti contiene un elenco dei computer utilizzati per eseguire il test. Sono visualizzati il nome del computer, il tempo processore in percentuale e la memoria disponibile. È possibile scegliere il nome di un computer per aprire il grafico **Controller e agenti** e verificare l'uso delle risorse nel tempo. Per altre informazioni, vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> È possibile comprimere ed espandere questa sezione scegliendo la freccia alla sinistra del titolo della sezione.

## <a name="errors"></a>Errori

La sezione contiene un elenco di tutti gli errori che si sono verificati durante il test di carico. Sono visualizzati il tipo e il sottotipo di errore, il conteggio e l'ultimo messaggio. È possibile scegliere un errore per aprire la tabella **Errori** ed esaminare altri dettagli sull'errore. Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) e [Procedura: Analizzare gli errori usando il pannello dei contatori](../test/how-to-analyze-errors-using-the-counters-panel.md).

> [!NOTE]
> È possibile comprimere ed espandere questa sezione scegliendo la freccia alla sinistra del titolo della sezione.

## <a name="printing-a-summary"></a>Stampa di un riepilogo

È possibile stampare il riepilogo del test di carico scegliendo **Stampa** dal menu di scelta rapida del riepilogo. Per visualizzare un'anteprima della stampa, scegliere **Anteprima di stampa** dal menu di scelta rapida del riepilogo. È anche possibile stampare direttamente dalla schermata di anteprima.

## <a name="see-also"></a>Vedere anche

- [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)