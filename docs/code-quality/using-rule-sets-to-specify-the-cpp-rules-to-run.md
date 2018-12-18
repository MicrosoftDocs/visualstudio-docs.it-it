---
title: Utilizzo di set di regole per specificare le regole C++ da eseguire
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ad464b11538dd8a3faf2bdf26cd7e3b2bc9650dd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Utilizzare i set di regole per specificare le regole di C++ per l'esecuzione

In Visual Studio, è possibile creare e modificare un oggetto personalizzato *set di regole* per soddisfare specifiche esigenze del progetto associate con l'analisi del codice. Per creare una regola personalizzata di C++ set, un progetto C/C++ deve essere aperto nell'IDE di Visual Studio. Quindi aprire un set di regole standard nell'editor set di regole e quindi aggiungere o rimuovere le regole specifiche e, facoltativamente, modificare l'azione che si verifica quando l'analisi del codice determina che è stata violata una regola.

Per creare una nuova regola personalizzata set, è necessario salvarlo con un nuovo nome file. Il set di regole personalizzato viene assegnato automaticamente al progetto.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Per creare una regola personalizzata da un singolo set di regole esistente

1. In Esplora soluzioni, aprire il menu di scelta rapida per il progetto e quindi scegliere **proprietà**.

2. Nel **proprietà** scegliere **analisi del codice**.

3. Nel **del Set di regole** elenco a discesa, effettuare una delle operazioni seguenti:

    - Scegliere il set di regole che si desidera personalizzare.

     \- oppure -

    - Scegliere  **\<Sfoglia... >** per specificare set di una regola esistente non è presente nell'elenco.

4. Scegliere **aprire** per visualizzare le regole nell'editor set di regole.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Per modificare una regola impostata nell'editor set di regole

- Per modificare il nome visualizzato del set di regole, scegliere il **vista** menu, scegliere **finestra proprietà**. Immettere il nome visualizzato nel **nome** casella. Si noti che il nome visualizzato può differire dal nome del file.

- Per aggiungere tutte le regole del gruppo a un set di regole personalizzato, selezionare la casella di controllo del gruppo. Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.

- Per aggiungere una regola specifica per il set di regole personalizzato, selezionare la casella di controllo della regola. Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.

- Per modificare l'azione eseguita quando viene violata una regola di analisi del codice, scegliere il **azione** campo per la regola e quindi scegliere uno dei valori seguenti:

     **Avvisa** -genera un avviso.

     **Errore** -genera un errore.

     **Nessuna** -disabilita la regola. Questa azione è quella della rimozione della regola dal set di regole.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Per raggruppare, filtrare o modificare i campi nell'editor set di regole utilizzando la barra degli strumenti editor set di regole

- Per espandere le regole in tutti i gruppi, scegliere **Espandi tutto**.

- Per comprimere le regole in tutti i gruppi, scegliere **Comprimi tutto**.

- Per modificare il campo che sono raggruppate le regole, scegliere il campo da di **Group By** elenco. Per visualizzare le regole separate, scegliere  **\<None >**.

- Per aggiungere o rimuovere i campi nelle colonne della regola, scegliere **Opzioni colonne**.

- Per nascondere le regole che non si applicano alla soluzione corrente, scegliere **nascondere regole che non si applicano alla soluzione corrente**.

- Per passare da visualizzare e nascondere le regole che vengono assegnate l'azione di errore, scegliere **Mostra regole che possono generare errori di analisi codice**.

- Per passare da visualizzare e nascondere le regole che vengono assegnate l'azione di avviso, scegliere **Mostra regole che possono generare avvisi di analisi codice**.

- Per visualizzare e nascondere regole che vengono assegnate i **Nessuno** azione, scegliere **Mostra regole che non sono abilitate**.

- Per aggiungere o rimuovere set di regole predefinite per il set di regole corrente di Microsoft, scegliere **Aggiungi o Rimuovi set di regole figlio**.