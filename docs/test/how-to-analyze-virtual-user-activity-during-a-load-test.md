---
title: Analizzare le attività degli utenti virtuali per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 3688b49a5e16d52ee569afe94569a705ead7f99c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Procedura: analizzare le attività degli utenti virtuali durante un test di carico utilizzando il grafico attività utente virtuale

Visualizzare l'attività utente virtuale associata al test di carico usando il Grafico attività utente virtuale. Ogni riga del grafico rappresenta un singolo utente virtuale. Il Grafico attività utente virtuale mostra esattamente l'attività eseguita da ogni utente virtuale durante il test. È possibile visualizzare modelli dell'attività utente, modelli di carico, test non riusciti o lenti correlati e richieste con altre attività utente virtuale. Il Grafico attività utente virtuale è disponibile solo al termine dell'esecuzione del test di carico.

Nelle procedure descritte di seguito viene illustrato come visualizzare il Grafico attività utente virtuale, come esaminare un'attività utente specifica e come usare il filtro.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Per visualizzare il Grafico attività utente virtuale nei risultati del test di carico

1.  Per visualizzare i dati utente virtuale, è necessario prima configurare l'impostazione **Tutti i singoli dettagli** per la proprietà **Intervallo archiviazione dettagli** associata al test di carico. Eseguire quindi il test di carico. Per altre informazioni, vedere [Procedura: Configurare la raccolta di dettagli completi per abilitare il grafico attività utente virtuale](../test/how-to-configure-load-tests-to-collect-full-details.md).

2.  Dopo l'esecuzione del test di carico, verrà visualizzata la pagina di riepilogo dei risultati del test. Scegliere il pulsante **Vai a dettagli utente** nella barra degli strumenti.

     oppure

     Aprire la visualizzazione Grafici scegliendo il pulsante **Grafici** nella barra degli strumenti. Fare clic con il pulsante destro del mouse su un grafico e scegliere **Vai a dettagli utente**.

     Se si utilizza questa opzione, al Grafico attività utente virtuale verrà applicato lo zoom automatico in modo da visualizzare la parte del test su cui è stato fatto clic con il pulsante destro del mouse. Se, ad esempio, il puntatore si trova approssimativamente sul contrassegno relativo ai 30 secondi, la visualizzazione dettagli verrà visualizzata approssimativamente in corrispondenza del contrassegno relativo ai 30 secondi nello strumento **Zoom periodo di tempo** nella parte inferiore del Grafico attività utente virtuale.

     È quindi possibile analizzare i dettagli di un'attività utente specifica nel Grafico attività utente virtuale.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Per analizzare un'attività utente specifica nel Grafico attività utente virtuale

1.  Utilizzare lo strumento Zoom periodo di tempo nella parte inferiore del Grafico attività utente virtuale per selezionare un'area del grafico in cui si desidera analizzare i dettagli per un utente specifico.

2.  Passare con il puntatore su un dettaglio nel grafico. Si noti che le informazioni seguenti vengono visualizzate nella descrizione comando:

    -   **ID utente**

    -   **Scenario**

    -   **Test**

    -   **URL** (non visualizzato in un test o in una transazione)

    -   **Risultato**

    -   **Browser** (non visualizzato in un test o in una transazione)

    -   **Network**

    -   **Ora di inizio**

    -   **Durata**

    -   **Agente**

    -   **Log test** (collegamento al log test)

        > [!NOTE]
        > Per facilitare il debug dell'applicazione, se si sceglie il collegamento Log test verrà visualizzato il risultato del test Web o dello unit test associato al log.

     È quindi possibile utilizzare le operazioni di filtro ed evidenziazione disponibili nel Grafico attività utente virtuale.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Per utilizzare le opzioni di filtro nel Grafico attività utente virtuale

1.  Nella Legenda dettagli usare l'elenco a discesa per selezionare **Test**, **Pagina** o **Transazione**.

     **Riquadro Legenda dettagli**

     ![Riquadro Legenda dettagli](../test/media/ltest_detailslegend.png "LTest_DetailsLegend")

2.  Selezionare o deselezionare le caselle di controllo relative a pagine ASPX, errori, log, test e ricerca associati al test di carico.

     Il Grafico attività utente virtuale verrà aggiornato di conseguenza.

     Il Grafico attività utente virtuale consente di filtrare test, pagine e transazioni in base ad alcuni criteri diversi. È ad esempio possibile rimuovere determinati test dalla visualizzazione, rimuovere tutti i test superati o rimuovere i test non superati a causa di errori specifici. È anche possibile rimuovere tutti i test che non dispongono di un log.

     Ad esempio, è possibile selezionare l'opzione **(Evidenzia errori)** per visualizzare tutti gli errori nel grafico in colore rosso. È anche possibile selezionare l'opzione **(Evidenzia risultati con log)** per visualizzare tutti i risultati del test nel grafico che dispongono di log in colore verde.

     **Riquadro Risultati filtro**

     ![Riquadro Risultati filtro](../test/media/ltest_filterresults.png "LTest_FilterResults")

3.  Nei risultati del filtro selezionare o deselezionare le caselle di controllo per le opzioni di filtro seguenti:

    -   **Mostra solo risultati con log** Vengono visualizzati solo i risultati dei test a cui è associato un log.

    -   **Mostra risultati corretti** Vengono visualizzati solo i risultati dei test superati.

    -   **Mostra risultati con errori** Vengono visualizzati i risultati in cui sono presenti errori, che possono risultare utili per l'esecuzione del debug.

        > [!NOTE]
        > È possibile analizzare ulteriormente l'elenco dei tipi di errore nel nodo **Mostra risultati con errori** scegliendo il pulsante Tabelle nella barra degli strumenti del Visualizzatore risultati test prestazioni Web. Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     Il Grafico attività utente virtuale verrà aggiornato di conseguenza.

## <a name="see-also"></a>Vedere anche

- [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Procedura dettagliata: uso del grafico attività utente virtuale per isolare i problemi](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)