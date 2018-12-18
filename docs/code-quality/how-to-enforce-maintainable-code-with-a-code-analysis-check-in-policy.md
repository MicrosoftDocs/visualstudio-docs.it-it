---
title: "Procedura: Applicare codice di facile manutenibilità con criteri di archiviazione dell'analisi del codice"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 339308675350bb6e4445b1dd068eb07d66f34164
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: applicare codice di facile manutenibilità con criteri di controllo dell'analisi codice

Gli sviluppatori possono utilizzare lo strumento di metrica del codice per misurare la complessità e della manutenibilità del codice, ma non è possibile richiamare la metrica del codice come parte di un criterio di controllo. Tuttavia, è possibile abilitare le regole di analisi del codice per verificare la conformità del codice con standard della metrica del codice e applicare le regole tramite criteri di archiviazione. Per ulteriori informazioni sulla metrica del codice, vedere [valori della metrica del codice](../code-quality/code-metrics-values.md).

È possibile abilitare la profondità dell'ereditarietà, accoppiamenti, indice di manutenibilità e le regole di complessità applicare il codice gestibile tramite criteri di controllo di analisi del codice. Le quattro di queste regole sono disponibili nella categoria "Regole di manutenibilità" nell'editor Criteri di analisi del codice.

Gli amministratori del controllo della versione di Team Foundation possono aggiungere le regole di manutenibilità di analisi codice per i requisiti dei criteri di archiviazione. Questi check-in criteri richiedono agli sviluppatori di eseguire l'analisi del codice in base a queste regole modificate prima dell'avvio di un controllo aggiuntivo.

## <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'editor Criteri di analisi codice

1. In **Team Explorer**, fare clic sul progetto team, fare clic su **impostazioni progetto Team**, quindi fare clic su **controllo del codice sorgente**.

     Il **controllo del codice sorgente** viene visualizzata la finestra di dialogo.

2. Nel **criteri di archiviazione** scheda e fare clic su **Aggiungi**.

     Il **aggiungere criteri di archiviazione** viene visualizzata la finestra di dialogo.

3. Nel **criteri di archiviazione** elenco, selezionare il **analisi del codice** casella di controllo e quindi fare clic su **OK**.

     Il **Editor criteri di analisi codice** viene visualizzata la finestra di dialogo.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di manutenibilità analisi codice

1. Nel **Editor criteri di analisi codice** nella finestra di dialogo **le impostazioni delle regole**, espandere il **regole di gestibilità** nodo.

2. Selezionare le caselle di controllo per le regole seguenti:

    -   Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** -soglia: più di 5 livelli di avviso

    -   Complessità: **CA1502 AvoidExcessiveComplexity** -soglia: avviso in più di 25.

    -   Indice di manutenibilità: **CA1505 AvoidUnmaintainableCode** -soglia: avviso in meno di 20

    -   Accoppiamenti di classi: **CA1506 AvoidExcessiveClassCoupling** -soglia: avviso più di 80 per una classe e più di 30 per un metodo

    Inoltre, se si desidera una violazione delle regole per evitare una compilazione corretta, selezionare il **considera gli avvisi come errori** casella di controllo accanto alla descrizione della regola.

3. Fare clic su **OK**. Il nuovo criterio si applica ora a future archiviazioni.

## <a name="see-also"></a>Vedere anche

- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
- [Creazione e utilizzo di criteri di controllo dell'analisi del codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)