---
title: Opzione&lt;T&gt; ActivityDesigner | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2bfdcc86531105e3b2c743a8aa0f88cda844efc7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="switchlttgt-activity-designer"></a>Opzione&lt;T&gt; ActivityDesigner
L'attività <xref:System.Activities.Statements.Switch%601> valuta un'espressione specificata e viene eseguita da una raccolta di attività la cui chiave associata corrisponde al valore ottenuto dalla valutazione.

 Il **Switch < T\>**  ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Switch%601> attività nella progettazione del flusso di lavoro di Windows.

## <a name="the-switchtactivity"></a>Il commutatore\<T > attività
 Un'attività <xref:System.Activities.Statements.Switch%601> contiene un oggetto <xref:System.Activities.Statements.Switch%601.Expression%2A> e un dizionario di <xref:System.Activities.Statements.Switch%601.Cases%2A>. Ogni caso nel dizionario è costituito da una coppia che contiene un *chiave* e un'attività che funge da corrispondente *valore*. L'attività <xref:System.Activities.Statements.Switch%601> valuta <xref:System.Activities.Statements.Switch%601.Expression%2A> e lo confronta con ogni chiave. Se viene rilevata una corrispondenza, viene eseguita l'attività corrispondente. È consentita una sola corrispondenza in quanto le chiavi del dizionario devono essere univoche in base al tipo di uguaglianza definito dall'operatore di confronto di uguaglianza del dizionario. Se non vengono rilevate corrispondenze, viene eseguita l'attività <xref:System.Activities.Statements.Switch%601.Default%2A>.

## <a name="how-to-use-the-switcht-activity-designer"></a>Come utilizzare l'opzione\<T > ActivityDesigner
 Il **commutatore\<T >** ActivityDesigner, vedere il **flusso di controllo** categoria del **della casella degli strumenti**, accessibile facendo clic di **Casella degli strumenti** scheda la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.) Dopo averlo rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], viene visualizzato il **Seleziona tipi di** finestra di dialogo per consentire all'utente di specificare il tipo generico *T* utilizzato <xref:System.Activities.Statements.Switch%601> attività. Il valore predefinito è **Int32**. Una volta il tipo generico *T* è stato selezionato un **Switch < T\>**  finestra di progettazione viene aggiunto nella finestra di progettazione del flusso di lavoro.

 Di seguito sono le proprietà di **Switch < T\>**  finestra di progettazione. Tutte le proprietà possono essere modificate nella griglia delle proprietà. Alcune di esse possono anche essere modificate nell'area della finestra di progettazione.

 La tabella seguente mostra le proprietà <xref:System.Activities.Statements.Switch%601> più utili e viene illustrato come usarle nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Switch%601>. Il valore predefinito è Switch < Int32\>. Il valore può essere modificato nel **proprietà** finestra o direttamente nell'intestazione della finestra di progettazione.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Specifica l'espressione usata per confrontare le chiavi presenti nella raccolta di case al fine da identificare il case da eseguire.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Se non vengono rilevate corrispondenze, specifica l'attività eseguita. Fare clic su di **aggiungere un'attività** pulsante nella finestra di progettazione per aprire la **predefinito** casella in cui è possibile rilasciare l'attività.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Specifica i case da valutare. Per aggiungere un case, fare clic su di **aggiungere nuovo case** pulsante nella parte inferiore della **commutatore\<T >** finestra di progettazione. Il pulsante diventa una casella di testo (casella combinata se il tipo generico selezionato durante l'aggiunta del commutatore\<T > è String o Enum). Dopo aver aggiunto una chiave di **caso valore** casella si espande l'area del case e un'attività può essere eliminata in cui il testo di suggerimento "Rilasciare l'attività" per definire la logica di esecuzione per il caso.|

 È possibile aggiungere più case, purché le relative chiavi non siano duplicate. In caso contrario, viene visualizzata una finestra di dialogo di errore in cui viene segnalato che la chiave del case specificata esiste già e che è necessario sceglierne un'altra. Nel **commutatore\<T >** della finestra di progettazione, area di un solo case può essere visualizzata in modalità espansa alla volta. Se l'area di un case si trova in modalità compressa, fare clic su di essa per espanderla. Si noti che, per un case compresso, nella finestra di progettazione viene mostrato l'eventuale nome visualizzato dell'attività a destra all'interno del case. In caso contrario, viene illustrato il **aggiungere un'attività** pulsante che consente di espandere il case fatto clic su di esso e consente di aggiungere un'attività.

 Fare clic sulla chiave del case esistente per trasformarla da etichetta in casella di testo in modo che sia possibile modificarla.

 È possibile eliminare un case in due modi.

1.  Selezionare il case ed eliminarlo.

2.  Selezionare il pulsante destro del mouse case, per visualizzare il menu di scelta rapida e selezionare **eliminare**.

 Si noti che è necessario selezionare il case per eliminarlo. La selezione e la deselezione dell'attività in un case riguardano la sola attività e non il case.

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)