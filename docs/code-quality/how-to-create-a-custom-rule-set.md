---
title: Creare una regola di analisi codice personalizzato impostata in Visual Studio
ms.date: 04/04/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9297d862b0fa47ecc4f5b7b08f6b754e1b5dfc3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="custom-rule-sets"></a>Set di regole personalizzate

È possibile creare un oggetto personalizzato *set di regole* per soddisfare specifiche esigenze del progetto per l'analisi codice.

## <a name="create-a-custom-rule-set"></a>Creare un set di regole personalizzate

Per creare una regola personalizzata set, è possibile aprire una regola predefinita impostata la **editor set di regole**. Da qui, è possibile aggiungere o rimuovere le regole specifiche ed è possibile modificare l'azione che si verifica quando una regola viene violata&mdash;, ad esempio, Mostra un avviso o un errore.

1. In **Esplora soluzioni**, fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **delle proprietà** pagine, selezionare il **analisi del codice** scheda.

3. Nel **eseguire il set di regole** elenco a discesa, effettuare una delle operazioni seguenti:

    - Selezionare il set di regole che si desidera personalizzare.

     \- oppure -

    - Selezionare  **\<Sfoglia... >** per specificare set di una regola esistente non è presente nell'elenco.

4. Selezionare **Open** per visualizzare le regole nell'editor set di regole.

È anche possibile creare un nuovo file di set di regole dal **nuovo File** finestra di dialogo:

1. Selezionare **File** > **nuovo** > **File**, o premere **Ctrl**+**N**.

2. Nel **nuovo File** finestra di dialogo, seleziona il **generali** categoria a sinistra e quindi selezionare **Set di regole di analisi codice**.

3. Selezionare **Apri**.

   Il nuovo *estensione ruleset* file verrà aperto nell'editor set di regole.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Creare una regola personalizzata impostata da più set di regole

1. In Esplora soluzioni, fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **delle proprietà** pagine, selezionare il **analisi del codice** scheda.

3. Selezionare  **\<scegliere più regola imposta... >** da **eseguire il set di regole**.

4. Nel **Aggiungi o Rimuovi set di regole** della finestra di dialogo selezionare i set di regole è da includere nel nuovo set di regole.

   ![Aggiungere o rimuovere la finestra di dialogo set di regole](media/add-remove-rule-sets.png)

5. Selezionare **Salva con nome**, immettere un nome per il *estensione ruleset* file e quindi selezionare **salvare**.

   Nuovo set di regole è selezionato nel **eseguire il set di regole** elenco.

6. Selezionare **aprire** per aprire il nuovo set di regole in editor set di regole.

## <a name="name-and-description"></a>Nome e descrizione

Per modificare il nome visualizzato di un set di regole che viene aperto nell'editor, aprire il **delle proprietà** selezionando **vista** > **finestra proprietà** nella barra dei menu. Immettere il nome visualizzato nel **nome** casella. È anche possibile immettere una descrizione per il set di regole.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver creato una regola impostata, il passaggio successivo consiste nel personalizzare le regole aggiungendo o rimuovendo le regole o modificando la gravità di violazioni delle regole.

> [!div class="nextstepaction"]
> [Modificare le regole di editor set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)