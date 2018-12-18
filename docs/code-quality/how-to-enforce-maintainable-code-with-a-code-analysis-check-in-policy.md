---
title: "Procedura: applicare codice di facile manutenibilità con criteri di controllo dell'analisi codice | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7ac4f31d1e93ed648bf2065bbff9dac8800c1d4f
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: Applicare codice di facile manutenibilità con criteri di archiviazione dell'analisi del codice

Gli sviluppatori possono utilizzare lo strumento di metrica del codice per misurare la complessità e della manutenibilità del codice, ma non è possibile richiamare la metrica del codice come parte di un criterio di controllo. Tuttavia, è possibile abilitare le regole di analisi del codice per verificare la conformità del codice standard di metrica del codice e applicare le regole tramite criteri di archiviazione. Per ulteriori informazioni sulla metrica del codice, vedere il [valori della metrica codice](../code-quality/code-metrics-values.md).

È possibile abilitare la profondità dell'ereditarietà, accoppiamenti, indice di manutenibilità e le regole di complessità applicare il codice gestibile tramite criteri di controllo di analisi del codice. Le quattro di queste regole sono disponibili nella categoria "Regole di manutenibilità" nell'editor Criteri di analisi del codice.

Gli amministratori del controllo della versione di Team Foundation possono aggiungere le regole di manutenibilità di analisi codice per i requisiti dei criteri di archiviazione. Questi check-in criteri richiedono agli sviluppatori di eseguire l'analisi del codice in base a queste regole modificate prima dell'avvio di un controllo aggiuntivo.

## <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'Editor criteri di analisi codice

1. in **Team Explorer**, fare clic sul progetto team, fare clic su **impostazioni progetto Team**, quindi fare clic su **controllo del codice sorgente**.

     The **Source Control** dialog box appears.

2. scegliere il **criteri di archiviazione** scheda e fare clic su **Aggiungi**.

     The **Add Check-in Policy** dialog box appears.

3. nel **criteri di archiviazione** elenco, selezionare il **analisi del codice** casella di controllo e quindi fare clic su **OK**.

     The **Code Analysis Policy Editor** dialog box appears.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di manutenibilità analisi codice

1. in il **Editor criteri di analisi codice** nella finestra di dialogo **le impostazioni delle regole**, espandere il **regole di gestibilità** nodo.

2. selezionare le caselle di controllo per le regole seguenti:

    -   Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** -soglia: più di 5 livelli di avviso

    -   Complessità: **CA1502 AvoidExcessiveComplexity** -soglia: avviso in più di 25.

    -   Indice di manutenibilità: **CA1505 AvoidUnmaintainableCode** -soglia: avviso in meno di 20

    -   Accoppiamenti di classi: **CA1506 AvoidExcessiveClassCoupling** -soglia: avviso più di 80 per una classe e più di 30 per un metodo

    Inoltre, se si desidera una violazione delle regole per evitare una compilazione corretta, selezionare il **considera gli avvisi come errori** casella di controllo accanto alla descrizione della regola.

3. fare clic su **OK**. Il nuovo criterio si applica ora a future archiviazioni.

## <a name="see-also"></a>Vedere anche

[Valori della metrica del codice](../code-quality/code-metrics-values.md)
[creazione e utilizzo di criteri di controllo dell'analisi del codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)