---
title: Violazioni di soglia per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, threshold violations
ms.assetid: 0126d7b7-0538-4ea9-9046-6556654b3b9d
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6acb9eec16107134dc03765da82008a01b599e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-analyze-threshold-violations-using-the-counters-panel-in-load-test-analyzer"></a>Procedura: analizzare le violazioni di soglia utilizzando il pannello dei contatori nell'Analizzatore test di carico

Il riquadro Contatori è visibile nella visualizzazione Grafici e nella visualizzazione Tabelle nell'analizzatore test di carico mentre è in esecuzione un test di carico o quando si analizza un risultato del test di carico. Vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md), [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) e [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md).

 Le violazioni di soglia sono associate a specifici contatori delle prestazioni e indicano che il contatore delle prestazioni ha superato o non ha raggiunto un valore soglia impostato. Tali violazioni di soglia vengono comunicate tramite icone nel riquadro Contatori.

 ![Nodo dei computer del pannello dei contatori](../test/media/ltest_compnode.png "LTest_CompNode")

 L'icona relativa a una violazione di soglia viene propagata dal nodo dell'albero dove risiede il contatore in errore fino al nodo radice. In questo modo si segnala all'utente una violazione in un contatore che potrebbe non essere visibile in un albero che non è stato espanso. Un esempio dell'icona può essere visualizzato nel nodo **Computer** nel pannello Contatori nella figura precedente.

 e possono essere una delle seguenti:

 ![Nessuna violazione di soglia](../test/media/icon_ltest_1.gif "Icon_LTest_1") Non si è verificata alcuna violazione di soglia.

 ![Violazione di soglia critica nell'ultimo intervallo](../test/media/icon_ltest_2.gif "Icon_LTest_2") Si è verificata una violazione di soglia critica nell'ultimo intervallo.

 ![Violazione di soglia critica in un intervallo precedente](../test/media/icon_ltest_3.gif "Icon_LTest_3") Si è verificata una violazione di soglia critica in un intervallo precedente.

 ![Violazione di soglia con avviso nell'ultimo intervallo](../test/media/icon_ltest_4.gif "Icon_LTest_4") Si è verificata una violazione di soglia con avviso nell'ultimo intervallo.

 ![Violazione di soglia con avviso in un intervallo precedente](../test/media/icon_ltest_5.gif "Icon_LTest_5") Si è verificata una violazione di soglia con avviso in un intervallo precedente.

## <a name="to-analyze-threshold-violations-in-the-counters-panel"></a>Per analizzare le violazioni di soglia nel riquadro Contatori

1.  Dopo il completamento di un test di carico o dopo il caricamento di un risultato di un test, scegliere **Grafici** o **Tabelle** nella barra degli strumenti dell'Analizzatore test di carico.

     Il pannello Contatori viene mostrato nella visualizzazione Grafici o nella visualizzazione Tabelle.

2.  Se il pannello Contatori non è visibile, fare clic su **Mostra pannello dei contatori** nella barra degli strumenti.

     In tutti i nodi contenenti violazioni di soglia sarà inclusa una delle icone elencate in precedenza.

3.  Espandere il nodo contenente un'icona della soglia, ad esempio il nodo **Computer**, come mostrato nella figura precedente del nodo Computer nel pannello Contatori con violazione di soglia. Continuare a espandere il nodo fino a raggiungere il contatore delle prestazioni con la violazione di soglia. Ad esempio, nella figura precedente viene illustrata l'istanza in errore di **Microsoft Virtual Machine Failed Bus Network Adapter**.

4.  (Facoltativo) Fare clic con il pulsante destro del mouse sul contatore delle prestazioni con la violazione di soglia e selezionare una delle opzioni seguenti:

    -   **Mostra contatore su grafico**: nella visualizzazione grafici, il contatore delle prestazioni è aggiunto ed evidenziato nel grafico selezionato. Per altre informazioni, vedere [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

        > [!NOTE]
        > Le icone relative alla violazione di soglia possono essere mostrate anche sul grafico nella visualizzazione Grafici. L'icona di soglia viene visualizzata nel grafico accanto al punto dati in cui si è verificata la violazione di soglia. Per eseguire questa operazione, scegliere l'elenco a discesa **Mostra legenda** nella barra degli strumenti e selezionare **Mostra violazioni di soglia su grafico**.

    -   **Mostra contatore su legenda**: nella legenda, il contatore delle prestazioni è aggiunto e selezionato. Per altre informazioni, vedere [Uso della legenda della visualizzazione Grafici per analizzare i test di carico](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Aggiungi grafico**:

    1.  Viene visualizzata la finestra di dialogo **Nome grafico**.

    2.  Immettere un nome per il nuovo grafico nella casella di testo **Nome grafico**, quindi scegliere **OK**.

    3.  (Facoltativo) Fare di nuovo clic con il pulsante destro del mouse sul contatore delle prestazioni e selezionare **Mostra contatore su grafico**.

         Per altre informazioni, vedere [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Facoltativo) Se si analizza la violazione di soglia in un risultato del test di carico completato, provare a utilizzare le funzionalità dello zoom nella visualizzazione Grafici. Per altre informazioni, vedere [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Se sono state rilevate violazioni di soglia durante l'esecuzione dei test di carico, si visualizzerà un collegamento denominato "violazioni di soglia", incluso il numero di violazioni, nella barra di stato dell'analizzatore test di carico. È possibile scegliere il collegamento per visualizzare tutte le violazioni di soglia nella tabella **Soglie** della visualizzazione Tabelle.

## <a name="see-also"></a>Vedere anche

- [Uso del pannello dei contatori nella visualizzazione Grafici e nella visualizzazione Tabelle](../test/counters-panel-in-load-test-analyzer.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)