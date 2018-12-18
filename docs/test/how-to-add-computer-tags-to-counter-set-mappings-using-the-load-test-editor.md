---
title: Aggiungere tag computer ai mapping degli insiemi di contatori per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 26a0ffc5835e79ee02d1041c4e228f59bcd87d37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>Procedura: aggiungere tag computer ai mapping dell'insieme di contatori utilizzando l'Editor test di carico

I tag computer consentono di identificare un computer con un nome facile da riconoscere e vengono visualizzati nel nodo **Mapping insiemi di contatori** nell'albero nell'Editor test di carico. Inoltre, i tag vengono visualizzati nei rapporti di Excel che consentono agli stakeholder di identificare il ruolo del computer nel test di carico. Ad esempio, "Web Server1 in lab2" o "SQL Server2 in Phoenix office". Per altre informazioni, vedere [Creazione di report sui risultati dei test di carico per confronti tra test o analisi delle tendenze](../test/compare-load-test-results.md).

## <a name="to-add-a-tag-to-a-computer"></a>Per aggiungere un tag a un computer

1.  Aprire un test di carico.

2.  Scegliere il pulsante **Gestisci insiemi di contatori**.

     - oppure -

     Fare clic con il pulsante destro del mouse sulla cartella **Insiemi di contatori** nell'albero del test di carico e scegliere **Gestisci insiemi di contatori**.

     Viene visualizzata la finestra di dialogo **Gestisci insiemi di contatori**.

3.  (Facoltativo) Nella casella di riepilogo **I computer e gli insiemi di contatori selezionati saranno aggiunti alla seguente impostazione di esecuzione** selezionare un'impostazione di esecuzione diversa.

    > [!NOTE]
    > Ciò vale solo se nel test di carico sono incluse più impostazioni di esecuzione.

4.  In **Computer e set di contatori da monitorare** selezionare il computer a cui si vuole applicare il tag.

    > [!NOTE]
    > Per informazioni su come aggiungere un computer, vedere [Procedura: Gestire insiemi di contatori](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

5.  Nella casella di testo **Tag computer** digitare un tag da associare al computer. Ad esempio, "TestMachine12 in lab3."

6.  Scegliere **OK**.

## <a name="see-also"></a>Vedere anche

- [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Procedura: Gestire insiemi di contatori](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)