---
title: Opzioni di tracciato per i contatori dei grafici per i test di carico in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 5df33a8cf05e4ad73b1643e2948392e49a32356e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382321"
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Procedura: Specificare le opzioni del tracciato per i contatori grafici

La finestra di dialogo **Opzioni tracciato** consente di modificare il colore e lo stile della linea di un contatore tracciato in un grafico. È possibile correggere anche l'intervallo a un valore specifico o impostare l'intervallo affinché venga regolato automaticamente in base ai dati campionati.

![Finestra di dialogo Opzioni tracciato](../test/media/ltest_plotoptions.png)

## <a name="to-specify-plotting-options-for-graphs"></a>Per specificare le opzioni relative ai tracciati per i grafici

1.  Nell'**Analizzatore test di carico** scegliere **Grafici** sulla barra degli strumenti del test di carico.

     I risultati del test di carico appaiono in una visualizzazione Grafici.

2.  Nella Legenda o nel grafico fare clic con il pulsante destro del mouse sulla riga o sulla linea del tracciato corrente del contatore delle prestazioni per il quale si vuole modificare l'opzione del tracciato, quindi selezionare **Opzioni tracciato**.

     Viene visualizzata la finestra di dialogo **Opzioni tracciato**.

3.  Usare l'elenco a discesa **Colore** per selezionare il colore che si vuole usare per il tracciato del contatore delle prestazioni.

4.  Usare l'elenco a discesa **Stile** per selezionare lo stile che si vuole usare per il tracciato del contatore delle prestazioni.

5.  Eseguire una delle operazioni seguenti:

     Selezionare **Regola automaticamente intervallo** (impostazione predefinita)

     \- oppure -

     Deselezionare **Regola automaticamente intervallo** e usare l'elenco a discesa **Intervallo** per specificare l'intervallo che si vuole usare per il tracciato del contatore delle prestazioni.

6.  Scegliere **OK**.

     Il contatore delle prestazioni per il quale sono state modificate le opzioni viene visualizzato nel grafico con le modifiche specificate.

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md)
