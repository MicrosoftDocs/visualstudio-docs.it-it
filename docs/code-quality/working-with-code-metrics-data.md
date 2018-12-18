---
title: La finestra Risultati metrica codice in Visual Studio
ms.date: 12/12/2017
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0053bcc23d8bb56a052e8d9203c08ce3ed17f2f9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="using-the-code-metrics-results-window"></a>Utilizzo della finestra Risultati metrica codice

Il **risultati metrica codice** finestra Visualizza i dati generati dall'analisi della metrica del codice. Per ulteriori informazioni sui valori di dati di metrica codice, vedere [valori della metrica del codice](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Visualizzazione risultati metrica codice

Il **risultati metrica codice** finestra viene visualizzata automaticamente quando si generano risultati metrica codice. È inoltre possibile visualizzare la finestra in qualsiasi momento.

### <a name="to-display-the-code-metrics-results-window"></a>Per visualizzare la finestra Risultati metrica codice

- Nel **Analizza** menu, scegliere **Windows** > **risultati metrica codice**.

   \- oppure -

- Nel **vista** menu, scegliere **altre finestre** > **risultati metrica codice**.

Il **risultati metrica codice** finestra viene visualizzata, anche se non contiene risultati.

### <a name="to-view-code-metrics-details"></a>Per visualizzare i dettagli sulla metrica del codice

Se sono stati generati risultati metrica codice, espandere l'albero di **gerarchia** colonna.

## <a name="filtering-code-metrics-results"></a>Filtro risultati metrica codice

È possibile filtrare i risultati vengono visualizzati di **risultati metrica codice** finestra utilizzando la barra degli strumenti nella parte superiore. Potrebbe ad esempio, si desidera visualizzare solo i risultati che includono un indice di manutenibilità inferiore a 65.

Il **filtro** casella di riepilogo a discesa contiene i nomi delle colonne di risultati. Quando viene definito un filtro, aggiungerlo alla fine dell'elenco con un rientro. L'elenco può contenere gli ultimi dieci filtri che sono stati definiti.

### <a name="to-filter-the-code-metrics-results"></a>Per filtrare i risultati della metrica codice

1.  Dal **filtro** , selezionare il nome della colonna.

2.  In **Min**, digitare il valore minimo da visualizzare.

3.  In **Max**, digitare il valore massimo deve essere visualizzato.

4.  Fare clic su di **Applica filtro** pulsante.

5.  Per visualizzare i dettagli dei risultati, espandere l'albero gerarchico.

## <a name="adding-removing-and-rearranging-data-columns"></a>Aggiungere, rimuovere e ridisporre le colonne di dati

È possibile aggiungere o rimuovere risultati le colonne di **risultati metrica codice** finestra. Inoltre, è possibile riorganizzare le colonne dei risultati in modo che vengano visualizzati nell'ordine in cui si desidera.

### <a name="to-remove-a-column"></a>Per rimuovere una colonna

1. Fare clic su di **Aggiungi/Rimuovi colonne** pulsante.

     \- oppure fare doppio clic su qualsiasi intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.

1. Nel **Aggiungi/Rimuovi colonne** la finestra di dialogo, deselezionare il casella di controllo per la colonna che si desidera rimuovere e quindi fare clic su **OK**.

### <a name="to-add-a-previously-removed-column"></a>Per aggiungere una colonna rimossa in precedenza

1. Fare clic su di **Aggiungi/Rimuovi colonne** pulsante.

     \- oppure -

     Fare doppio clic su qualsiasi intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.

1. Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la casella di controllo per la colonna che si desidera aggiungere e quindi fare clic su **OK**.

### <a name="to-rearrange-columns"></a>Per riordinare le colonne

1. Fare clic su di **Aggiungi/Rimuovi colonne** pulsante.

     \- oppure -

     Fare doppio clic su qualsiasi intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.

1. Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la colonna che si desidera spostare e quindi fare clic sulla freccia in su o freccia in giù.

1. Quando la colonna si trova in cui si desidera, fare clic su **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Copia dei dati negli Appunti o Excel

È possibile selezionare e copiare una riga selezionata di dati di metrica codice negli Appunti come una stringa di testo che contiene una riga per il nome e il valore di ogni colonna di dati. È anche possibile fare clic su **Apri selezione in Microsoft Excel** per esportare tutti i risultati della metrica codice in un foglio di calcolo di Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Creazione di un elemento di lavoro in base ai risultati metrica codice

È possibile creare un [Visual Studio Team Services (VSTS)](/vsts/index) elemento di lavoro che si basa sul comporta il **risultati metrica codice** finestra. Quando viene creato l'elemento di lavoro, Visual Studio inserisce automaticamente un titolo nel **titolo** dati di metrica del campo e il codice sotto il **cronologia** scheda.

Per ulteriori informazioni su Visual Studio Team Services, gli elementi di lavoro, vedere [(VSTS) di elementi di lavoro](/vsts/work/work-items/index).

### <a name="to-create-a-work-item-based-on-a-result"></a>Per creare un elemento di lavoro basato su un risultato

1.  Fare clic sul risultato.

2.  Scegliere **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare (**Bug**, **attività**e così via).

3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.

4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.

### <a name="to-create-a-bug-based-on-a-result"></a>Per creare un bug basato su un risultato

1.  Fare clic sul risultato per selezionarlo.

2.  Fare clic su di **Crea elemento di lavoro** pulsante.

3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.

4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.

## <a name="see-also"></a>Vedere anche

- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
- [Procedura: generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)