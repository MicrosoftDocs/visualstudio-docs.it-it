---
title: Analisi dell'attività utente virtuale del test di carico in Visual Studio | Microsoft Docs
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 5f874b070e726374a20e821508115b5798f40b80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analisi dell'attività utente virtuale del test di carico nella visualizzazione Dettagli dell'Analizzatore test di carico

**Grafico attività utente virtuale**

 ![Grafico attività utente virtuale](../test/media/virtual_actchart.png "Virtual_ActChart")

 La visualizzazione Dettagli consente di visualizzare il Grafico attività utente virtuale, usato per analizzare visivamente le attività eseguite dai singoli utenti virtuali durante il test di carico. Il Grafico attività utente virtuale consente di visualizzare modelli dell'attività utente, modelli di carico, test non riusciti o lenti correlati e richieste con altra attività utente virtuale. Il Grafico attività utente virtuale consente inoltre di determinare i picchi di utilizzo della CPU, le cadute di richieste al secondo e i test o le pagine in esecuzione durante tali picchi o cadute.

> [!NOTE]
> Prima di eseguire il test di carico per il quale si desidera utilizzare il grafico dei dettagli relativi all'attività utente virtuale, è necessario verificare che la proprietà **Intervallo archiviazione dettagli** sia impostata su **AllIndividualDetails** utilizzando l'Editor test di carico. Per altre informazioni, vedere [Procedura: Configurare la raccolta di dettagli completi per abilitare il grafico attività utente virtuale](../test/how-to-configure-load-tests-to-collect-full-details.md).

 **Riquadro Legenda dettagli**

 ![Riquadro Legenda dettagli](../test/media/ltest_detailslegend.png "LTest_DetailsLegend")

 Il riquadro Legenda dettagli è visibile nel Grafico attività utente virtuale. Il riquadro Legenda dettagli consente di filtrare test, pagine e transazioni in base a diversi criteri. È ad esempio possibile rimuovere determinati test dalla visualizzazione, rimuovere tutti i test superati o rimuovere i test non superati a causa di errori specifici. È anche possibile rimuovere tutti i test che non dispongono di un log.

 È possibile evidenziare i test non superati, in modo che vengano visualizzati in rosso. È inoltre possibile evidenziare i test che dispongono di log. Tali test verranno visualizzati in verde.

 **Riquadro Risultati filtro**

 ![Riquadro Risultati filtro](../test/media/ltest_filterresults.png "LTest_FilterResults")

 Il riquadro Risultati filtro è visibile nel Grafico attività utente virtuale. Il pannello Risultati filtro può essere usato per filtrare in base ai seguenti criteri:

-   **Mostra solo risultati con log** Vengono visualizzati solo i risultati dei test a cui è associato un log.

-   **Mostra risultati corretti** Vengono visualizzati solo i risultati dei test superati.

-   **Mostra risultati con errori** Vengono visualizzati i risultati in cui sono presenti errori che possono risultare utili per l'esecuzione del debug.

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Configurare il test di carico per utilizzare il Grafico attività utente virtuale:** prima di eseguire un test di carico in cui si desidera visualizzare i dati dell'attività utente virtuale, è necessario configurare le impostazioni delle proprietà del test di carico.|-   [Procedura: Configurare la raccolta di dettagli completi per abilitare il grafico attività utente virtuale](../test/how-to-configure-load-tests-to-collect-full-details.md)|
|**Eseguire il test di carico:** dopo che un test di carico è stato creato e configurato per abilitare la raccolta dati dell'attività utente virtuale, è necessario eseguire il test fino al completamento per visualizzare il Grafico attività utente virtuale.||
|**Visualizzare i risultati del test di carico contenenti i dati dell'attività utente virtuale:** dopo aver creato e configurato un test di carico e averne completata l'esecuzione, è possibile visualizzare i dati dell'attività utente virtuale utilizzando il Grafico attività utente virtuale.|-   [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Procedura: Analizzare le attività degli utenti virtuali durante un test di carico](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isolare i problemi di prestazioni nei test di carico:** è possibile utilizzare il Grafico attività utente virtuale per isolare i problemi di prestazioni nel test di carico.|-   [Procedura dettagliata: Utilizzo del grafico attività utente virtuale per isolare i problemi](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)