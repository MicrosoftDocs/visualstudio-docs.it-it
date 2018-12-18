---
title: Utilizzare l'Editor di Set di regole di analisi codice in Visual Studio
ms.date: 04/-4/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bd9f02142b803cc9a09fce79cb687ea521dea9e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Utilizzare l'editor di set di regole di analisi codice

Editor set di regole di analisi codice consente di specificare le regole che sono inclusi in un set di regole personalizzato e la gravità di violazioni delle regole.

|Azione (gravità)|Descrizione|
|-|-|
|Avviso|Genera un avviso nel **elenco errori** e anche in fase di compilazione.|
|Error|Genera un errore nel **elenco errori** e anche in fase di compilazione.|
|Info|Genera un messaggio nel **elenco errori**.|
|Hidden|La violazione non è visibile all'utente. L'IDE riceve una notifica della violazione, tuttavia.|
|Nessuno|La regola viene eliminata. Il comportamento è lo stesso come se la regola è stato rimosso dal set di regole.|

L'editor visualizza le regole in una struttura ad albero che set di gruppi di regole da una regola di campo specificato. Per aggiungere o rimuovere le regole da un set di regole, eseguire una o più delle seguenti operazioni:

- Selezionare o deselezionare la casella di controllo del nodo di gruppo per aggiungere o rimuovere tutte le regole nel gruppo. Quando si seleziona un gruppo, tutte le regole sono impostate le **avviso** azione.

   > [!TIP]
   > È possibile modificare come le regole sono raggruppate nel **raggruppare** elenco a discesa.

- Fare clic su di **azione** campo di un gruppo, quindi specificare l'azione da applicare a tutte le regole nel gruppo.

- Selezionare o deselezionare la casella di controllo per una singola regola. Quando si seleziona la casella di controllo per una regola, la regola è impostata per l'azione di avviso.

## <a name="toolbar"></a>ToolBar

È possibile utilizzare la barra degli strumenti dell'editor set di regole per raggruppare, filtrare e cercare i dati visualizzati nella griglia di set di regole.

Nella tabella seguente vengono descritti i controlli sulla barra degli strumenti dell'editor set di regole.

|Controllo ToolBar|Descrizione|
|---------------------|-----------------|
|**Espandi tutto**|Vengono illustrate le regole in tutti i gruppi.|
|**Comprimi tutto**|Nasconde le regole in tutti i gruppi.|
|**Group By**|Specifica il campo da cui le regole sono raggruppate. Fare clic su  **\<None >** per mostrare le regole senza gruppi.|
|**Opzioni colonne**|Specifica i campi della regola da visualizzare.|
|**Nascondi le regole che non si applicano alla soluzione corrente**|Mostra o nasconde le regole che non sono dello stesso tipo di destinazione della soluzione.|
|**Mostra regole che possono generare errori di analisi del codice**|Mostra o nasconde le regole che vengono assegnate l'azione di errore.|
|**Mostra regole che possono generare avvisi di analisi del codice**|Mostra o nasconde le regole che vengono assegnate l'azione di avviso.|
|**Mostra regole non abilitate**|Mostra o nasconde le regole che vengono assegnate None azione.|
|**Aggiungere o rimuovere set di regole figlio**|Aggiunge o rimuove le regole nei set di regole selezionato.|
|**Regole di ricerca**|Cerca tutti i valori di campo per la stringa specificata.|

## <a name="rule-set-fields"></a>I campi del set di regole

Campi di set di regole visualizzano informazioni su un set di regole e possono essere utilizzati per ordinare e raggruppare l'elenco di regole. Per visualizzare o nascondere i campi, selezionare **Opzioni colonne** sulla regola set degli strumenti dell'editor e quindi selezionare o deselezionare le caselle di controllo dei campi per mostrare o nascondere.

Nella tabella seguente descrive i campi di un set di regole:

|Campo|Descrizione|
|-----------|-----------------|
|**ID**|Identificatore della regola.|
|**Categoria**|Oltre all'appartenenza a set di regole, regole di analisi del codice vengono raggruppate per categoria. Per altre informazioni, vedere [gli avvisi di analisi del codice](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Il titolo della regola.|
|**Spazio dei nomi**|Lo spazio dei nomi della regola.|
|**Tipo di destinazione**|Indica se la regola per nativo, gestito o codice di database.|
|**Azione**|L'azione eseguita quando la regola viene violata in un'esecuzione dell'analisi codice. È possibile modificare il **azione** campo.|
|**Set di regole di origine**|Il set di regole che contiene la regola.|

## <a name="sort-and-filter-rule-sets"></a>Ordina e filtra set di regole

Dalle intestazioni di colonna della griglia di set di regole, è possibile ordinare e filtrare le regole in base ai valori del campo.

- Per ordinare gli elenchi di set di regole, fare clic sull'intestazione di colonna del campo da cui si desidera ordinare. Se il set di regole sono raggruppate, ogni gruppo viene ordinato singolarmente.

- Per filtrare i set di regole per il valore di un campo, fare clic sul pulsante filtro nell'intestazione di colonna del campo da cui si desidera filtrare. Selezionare le caselle di controllo dei valori di che si desidera visualizzare e deselezionare le caselle di controllo dei valori di che si desidera nascondere.

## <a name="see-also"></a>Vedere anche

- [Creare un set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md)