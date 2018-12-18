---
title: 'Procedura: creare un Set di regole personalizzato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3095d5eff59506f3d7681f61f11f73d37258647d
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-create-a-custom-rule-set"></a>Procedura: Creare un set di regole personalizzato

In Visual Studio, è possibile creare e modificare un oggetto personalizzato *set di regole* per soddisfare specifiche esigenze del progetto associate con l'analisi del codice. Per creare una regola personalizzata impostata, si apre uno o più standard regola imposta nell'editor set di regole. È quindi possibile aggiungere o rimuovere le regole specifiche ed è possibile modificare l'azione che si verifica quando l'analisi del codice determina che è stata violata una regola.

 Per creare una nuova regola personalizzata set, è necessario salvarlo con un nuovo nome file. Il set di regole personalizzato viene assegnato automaticamente al progetto.

## <a name="opening-the-rule-set-editor"></a>Editor set di apertura della regola

### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Per aprire un oggetto vuoto del set di regole file nell'editor set di regole

1. Nel **File** dal menu di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], scegliere **New** e quindi fare clic su **File**.

2. Nel **nuovo File** la finestra di dialogo, fare clic su **generale** nel **modelli installati** elenco e quindi selezionare **Set di regole di analisi codice**.

3. Viene visualizzato l'editor set di regole. Nessuna regola viene selezionata nell'elenco dell'editor.

### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Per creare una regola personalizzata da un singolo set di regole esistente

1. In Esplora soluzioni, fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **proprietà** scheda, fare clic su **analisi del codice**.

3. Nel **del Set di regole** elenco a discesa, effettuare una delle operazioni seguenti:

    - Selezionare il set di regole che si desidera personalizzare.

     \- oppure -

    - Selezionare  **\<Sfoglia... >** per specificare set di una regola esistente non è presente nell'elenco.

4. Fare clic su **aprire** per visualizzare le regole nell'editor set di regole.

### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Per creare una regola personalizzata set da più set di regole esistente

1. In Esplora soluzioni, fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **proprietà** scheda, fare clic su **analisi del codice**.

3. Selezionare  **\<scegliere più regola imposta... >** da **eseguire il set di regole**.

4. Nel **Aggiungi o Rimuovi set di regole** nella finestra di dialogo Seleziona i set di regole in cui si desidera basare il nuovo set di regole e quindi fare clic su **OK**.

5. Salvare il nuovo set di regole.

     Viene selezionato il nome del nuovo set di regole nel **eseguire il set di regole** elenco. È possibile modificare il nome visualizzato della regola impostata nel passaggio successivo.

6. (Facoltativo) Per modificare il nome visualizzato del set di regole, scegliere il **vista** menu, fare clic su **finestra proprietà**. Digitare il nome visualizzato nel **nome** casella.

7. Per aggiungere, rimuovere, o modificare le regole di analisi codice specifico del nuovo set di regole, fare clic su **aprire**.

## <a name="modifying-a-rule-set"></a>Modifica di un set di regole

### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Per modificare una regola impostata nell'editor set di regole

- Per modificare il nome visualizzato del set di regole, scegliere il **vista** menu, fare clic su **finestra proprietà**. Immettere il nome visualizzato nel **nome** casella. Si noti che il nome visualizzato può differire dal nome del file.

- Per aggiungere tutte le regole del gruppo a un set di regole personalizzato, selezionare la casella di controllo del gruppo. Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.

- Per aggiungere una regola specifica per il set di regole personalizzato, selezionare la casella di controllo della regola. Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.

- Per modificare l'azione eseguita quando viene violata una regola di analisi del codice, fare clic nel **azione** campo per la regola, quindi selezionare uno dei valori seguenti:

     **Avvisa** -genera un avviso.

     **Errore** -genera un errore.

     **Nessuna** -disabilita la regola. Questa azione è quella della rimozione della regola dal set di regole.

## <a name="changing-the-rule-set-editor-display"></a>Modifica la regola di visualizzazione dell'editor set

### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Per raggruppare, filtrare o modificare i campi nell'editor set di regole utilizzando la barra degli strumenti editor set di regole

- Per espandere le regole in tutti i gruppi, fare clic su **Espandi tutto**.

- Per comprimere le regole in tutti i gruppi, fare clic su **Comprimi tutto**.

- Per modificare il campo che sono raggruppate le regole, selezionare il campo da di **Group By** elenco. Per visualizzare le regole separate, selezionare  **\<None >**.

- Per aggiungere o rimuovere i campi nelle colonne della regola, fare clic su **Opzioni colonne**.

- Per nascondere le regole che non si applicano alla soluzione corrente, **nascondere regole che non si applicano alla soluzione corrente**.

- Per visualizzare e nascondere le regole che vengono assegnate l'azione di errore, fare clic su **Mostra regole che possono generare errori di analisi codice**.

- Per visualizzare e nascondere le regole che vengono assegnate l'azione di avviso, fare clic su **Mostra regole che possono generare avvisi di analisi codice**.

- Per visualizzare e nascondere regole che vengono assegnate i **Nessuno** azione, fare clic su **Mostra regole che non sono abilitate**.

- Per aggiungere o rimuovere set di regole predefinite per il set di regole corrente di Microsoft, fare clic su **Aggiungi o Rimuovi set di regole figlio**.

## <a name="see-also"></a>Vedere anche

[Procedura: configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
[riferimento del set di regole di analisi codice](../code-quality/code-analysis-rule-set-reference.md)