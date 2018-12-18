---
title: Analisi dei risultati dei test di carico in Visual Studio | Microsoft Docs
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7add3789d3c48fb405818f50efd47bb83cb9f899
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analizzare i risultati dei test di carico tramite l'Analizzatore test di carico

Trovare colli di bottiglia, identificare errori e misurare i miglioramenti dell'applicazione usando l'Analizzatore test di carico. Analizzare i risultati del test di carico nei modi seguenti:

-   Monitorare un test di carico mentre è in esecuzione.

-   Analizzare un test di carico dopo che è stato completato.

-   Visualizzare i risultati di un test di carico precedente.

È inoltre possibile creare rapporti per confrontare due o più rapporti o per eseguire l'analisi delle tendenze da condividere con gli stakeholder. Vedere [Creazione di report sui risultati dei test di carico per confronti tra test o analisi delle tendenze](../test/compare-load-test-results.md).

È possibile completare queste attività sia che il test di carico venga eseguito da Visual Studio Enterprise o dalla riga di comando, sia che venga eseguito in un singolo computer o in un computer remoto.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Differenze tra l'analisi di un test di carico in esecuzione e l'analisi di un test di carico completato

 Quando si esegue un test di carico, l'Analizzatore test di carico viene visualizzato in una scheda separata, insieme al nome del test di carico e all'ora in cui il test ha avuto inizio (ad esempio, **LoadTest1 [12:40 PM]**). Quando un test di carico è in esecuzione, in memoria viene mantenuto un insieme ridotto di dati dei contatori delle prestazioni che è possibile monitorare. Dopo il completamento di un test di carico, è possibile analizzare l'intero insieme di dati dal database. Esistono alcune differenze nei dati che vengono visualizzati durante o dopo l'esecuzione di un test di carico. Ad esempio, il 90% e il 95% dei dati relativi al tempo di risposta non viene calcolato finché il test di carico non è stato completato. Vi sono inoltre alcune differenze nelle funzionalità degli strumenti, disponibili per l'analisi dei dati.

 Quando si esegue il test di carico, sono disponibili due visualizzazioni: la visualizzazione Grafici e la visualizzazione Tabelle. La visualizzazione Grafici consente all'utente di rappresentare in un grafico i contatori delle prestazioni raccolti. La visualizzazione Tabelle fornisce informazioni su ciascun test, pagina, transazione e richiesta raccolti. È possibile anche ottenere una tabella in cui sono elencati gli errori.

 Per impostazione predefinita, quando l'esecuzione dei test di carico è stata completata, viene mostrata la visualizzazione Riepilogo. È possibile passare tra le visualizzazioni Riepilogo, Grafici, Tabelle e Dettagli utilizzando la barra degli strumenti. L'Analizzatore test di carico può essere ancorato o lasciato mobile usando le consuete tecniche di manipolazione delle finestre di Visual Studio. Quando si analizzano esecuzioni di test completate, è possibile avere più analizzatori test di carico aperti simultaneamente per confrontare le diverse esecuzioni di test.

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Accesso ai risultati del test di carico:** quando si esegue un test di carico dall'Editor test di carico, i risultati del test vengono aperti automaticamente e il test di carico in esecuzione viene visualizzato nell'Analizzatore test di carico.|-   [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md)|
|**Aggiungere note di analisi al test di carico:** è possibile aggiungere commenti al test di carico quando si conduce l'analisi. I commenti vengono archiviati in modo permanente, insieme al risultato del test di carico. La descrizione immessa viene visualizzata anche nella colonna **Descrizione** associata al test di carico nella finestra di dialogo Apri e gestisci risultati test di carico nell'Editor test di carico.<br /><br /> Per altre informazioni, vedere [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> I commenti vengono inoltre visualizzati quando si crea un rapporto di Excel per i risultati del test di carico.<br /><br /> Per altre informazioni, vedere [Creazione di report sui risultati dei test di carico per confronti tra test o analisi delle tendenze](../test/compare-load-test-results.md).|-   [Procedura: Aggiungere commenti mentre si analizza un test di carico completato](../test/how-to-add-comments-on-a-completed-load-test.md)|
|**Analisi dei risultati del test di carico:** dopo l'accesso ai dati dell'esecuzione del test di carico, è possibile analizzare i dati risultanti. È possibile visualizzare il riepilogo del test di carico per comprendere rapidamente i risultati. Nel riepilogo dei test di carico vengono riportati i risultati principali in un formato compatto e di agevole lettura.<br /><br /> Il riepilogo può anche essere stampato. per comunicare più agevolmente i risultati dei test di carico agli stakeholder.<br /><br /> È possibile analizzare i dettagli dei risultati del test di carico utilizzando i grafici e le tabelle nei risultati. Le tabelle disponibili sono le seguenti: Errori, Pagine, Richieste, Traccia SQL, Test, Soglie e Transazioni.|-   [Cenni preliminari sul riepilogo dei risultati dei test di carico](../test/load-test-results-summary-overview.md)<br />-   [Procedura: Visualizzare la risposta delle pagine Web](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analisi dell'attività utente virtuale nei risultati del test di carico per isolare i problemi di prestazioni:** è possibile utilizzare il Grafico attività utente virtuale per visualizzare l'attività degli utenti virtuali durante un test di carico. In questo modo, è possibile isolare i picchi di utilizzo della CPU o le cadute di richieste al secondo e determinare quali test o pagine sono in esecuzione durante tali picchi o cadute.|-   [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|