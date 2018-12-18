---
title: Analizzare gli errori dei test di carico usando il pannello dei contatori in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 2705120f5cf0e13e94369140c256bd3c7ae1466b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>Procedura: analizzare gli errori utilizzando il pannello dei contatori

Il riquadro Contatori è visibile nella visualizzazione Grafici e nella visualizzazione Tabelle nell'analizzatore test di carico mentre è in esecuzione un test di carico o quando si analizza un risultato del test di carico. Per altre informazioni, vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md), [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) e [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md).

 Il nodo **Errori** nel pannello dei contatori contiene tutti gli errori rilevati durante il test di carico. Il nodo Errori contiene inoltre diverse sottocategorie di nodi di errori, specifiche per diversi tipi di errori, ad esempio **eccezioni** ed **errori HTTP**.

 ![Nodo degli errori del pannello dei contatori](../test/media/ltest_errornode.png "LTest_ErrorNode")

## <a name="to-analyze-errors-in-the-counters-panel"></a>Per analizzare gli errori nel riquadro Contatori

1.  Dopo il completamento di un test di carico o dopo il caricamento di un risultato di un test, scegliere **Grafici** o **Tabelle** nella barra degli strumenti dell'Analizzatore test di carico.

     Il pannello **Contatori** viene visualizzato nella visualizzazione Grafici o nella visualizzazione Tabelle.

2.  Se il pannello Contatori non è visibile, fare clic su **Mostra pannello dei contatori** nella barra degli strumenti.

3.  Espandere **Errori** e selezionare una categoria o una sottocategoria di errore da analizzare.

4.  Fare clic con il pulsante destro del mouse sull'errore e scegliere una delle seguenti opzioni:

    -   **Mostra contatore su grafico**: nella visualizzazione Grafici l'errore viene aggiunto ed evidenziato nel grafico selezionato. Per altre informazioni, vedere [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

    -   **Mostra contatore su legenda**: l'errore viene aggiunto e selezionato nella legenda. Per altre informazioni, vedere [Uso della legenda della visualizzazione Grafici per analizzare i test di carico](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Aggiungi grafico**:

    1.  Viene visualizzata la finestra di dialogo **Nome grafico**.

    2.  Immettere un nome per il nuovo grafico nella casella di testo **Nome grafico**, quindi scegliere **OK**.

    3.  (Facoltativo) Fare di nuovo clic con il pulsante destro del mouse sull'errore e selezionare **Mostra contatore su grafico**.

         Per altre informazioni, vedere [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Facoltativo) Se si analizza l'errore in un risultato del test di carico completato, provare a utilizzare le funzionalità dello zoom nella visualizzazione Grafici. Per altre informazioni, vedere [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Se sono stati rilevati errori durante l'esecuzione dei test di carico, viene visualizzato un collegamento denominato "errori", insieme al numero di errori, nella barra di stato dell'analizzatore test di carico. È possibile scegliere il collegamento per visualizzare tutti gli errori nella tabella **Errori** della visualizzazione Tabelle.

## <a name="see-also"></a>Vedere anche

- [Uso del pannello dei contatori nella visualizzazione Grafici e nella visualizzazione Tabelle](../test/counters-panel-in-load-test-analyzer.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)