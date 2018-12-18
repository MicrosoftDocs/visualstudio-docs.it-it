---
title: Uso della legenda della visualizzazione Grafici per analizzare i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: a6c14375d46c4317b86b9da67526230369cfbcb6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-graphs-view-legend-to-analyze-load-tests"></a>Utilizzo della legenda della visualizzazione Grafici per analizzare i test di carico

Nella visualizzazione Grafici dell'analizzatore test di carico è incluso un riquadro legenda in cui vengono visualizzate le informazioni per ogni contatore delle prestazioni associato al grafico attualmente selezionato.

![Legenda visualizzazione Grafici](../test/media/load_viewlegend.png "Load_ViewLegend")

Nella legenda sono contenute le informazioni seguenti:

-   **Visualizzazione nel grafico:** usare le caselle di controllo per specificare se la linea relativa a un particolare contatore, ad esempio **Carico utente** o **Errori/sec**, viene tracciata sul grafico. Selezionare una casella di controllo se si desidera che la relativa riga venga tracciata nel grafico. Per rimuovere una linea del tracciato dal grafico, deselezionare la relativa casella di controllo. Quando viene rimossa una linea del tracciato, le statistiche per il contatore continuano ad essere visualizzate nella legenda.

-   **Intervallo:** in questa colonna viene visualizzato l'intervallo dell'asse y del contatore delle prestazioni. Per impostazione predefinita, questo valore verrà regolato automaticamente secondo le modifiche all'intervallo dei dati di esempio. Un intervallo regolato automaticamente sarà sempre maggiore di una potenza di 10 rispetto al valore Max. Ciò include potenze di 10 negative. Un grafico può contenere una varietà di contatori, ciascuno con un intervallo diverso. Pertanto, l'asse y non è identificato da nessun intervallo specifico, ma è identificato da valori da 0 a 100 che rappresentano una percentuale dell'intervallo totale per ciascun contatore. Per un contatore con un intervallo di 1000, ad esempio, un punto dati di 60 sull'asse y corrisponderebbe a un valore di 600 per il contatore.

    > [!NOTE]
    > È possibile disabilitare la regolazione automatica del valore di intervallo bloccando l'intervallo su un valore specifico. Quando viene bloccato l'intervallo, qualsiasi valore che lo superi verrà visualizzato come valore massimo specificato all'inizio del grafico. Usare la finestra di dialogo **Opzioni tracciato** per bloccare l'intervallo su un valore specifico. Per altre informazioni, vedere [Procedura: Specificare le opzioni del tracciato per i contatori grafici](../test/how-to-specify-plot-options-for-graphing-counters.md).

-   **Contatore:** le quattro colonne denominate **Contatore**, **Istanza**, **Categoria** e **Computer** identificano insieme in modo univoco il contatore delle prestazioni.

-   **Colore:** nella colonna **Colore** vengono visualizzati il colore e lo stile della linea del tracciato per il contatore delle prestazioni. La finestra di dialogo **Opzioni tracciato** consente di modificare il colore o lo stile della linea di un contatore delle prestazioni nel grafico. La finestra di dialogo **Opzioni tracciato** è disponibile dal menu di scelta rapida della legenda. Per altre informazioni, vedere [Procedura: Specificare le opzioni del tracciato per i contatori grafici](../test/how-to-specify-plot-options-for-graphing-counters.md).

-   **Statistiche:** nelle colonne **Min**, **Max**, **Media** e **Ultimo** vengono visualizzate le rispettive statistiche per il contatore delle prestazioni. I valori corrispondono ai dati visualizzati nell'area visibile del grafico. Se ad esempio, si ingrandisce l'area di un'esecuzione, le statistiche della legenda riporteranno valori solo per l'area ingrandita. La colonna "Ultimo" corrisponde al valore del contatore delle prestazioni dell'intervallo di campionamento completato più recentemente.

    > [!NOTE]
    > La colonna Ultimo viene visualizzata solo nella legenda dell'analizzatore test di carico mentre il test è in esecuzione.

     Per altre informazioni, vedere [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

La selezione di un elemento nella legenda consente di effettuare le operazioni seguenti:

-   Consente la rimozione dell'elemento dalla legenda e dal grafico. Fare clic con il pulsante destro del mouse su un elemento e scegliere **Elimina** oppure premere **CANC**.

-   Consente di evidenziare la linea del tracciato nel grafico.

-   Consente di visualizzare i dati per l'elemento selezionato nella griglia dei dati.

-   Consente di accedere alla finestra di dialogo **Opzioni tracciato** per il contatore.

> [!TIP]
> È possibile usare il pulsante del menu a discesa **Opzioni grafico** sulla barra degli strumenti Analizzatore test di carico e selezionare **Mostra legenda** per visualizzare o nascondere il riquadro **Legenda** associato alla visualizzazione del grafico.

## <a name="see-also"></a>Vedere anche

- [Procedura: Specificare le opzioni del tracciato per i contatori grafici](../test/how-to-specify-plot-options-for-graphing-counters.md)
- [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)