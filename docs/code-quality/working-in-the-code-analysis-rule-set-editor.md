---
title: Utilizzo di regole di analisi codice Editor Set | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c832b29512bfd7339ab60044ece81f1626be9bc7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Utilizzo dell'editor set di regole di analisi del codice
Editor set di regole di analisi del codice consente di specificare le regole che sono inclusi in un set di regole personalizzate e di specificare l'azione. È inoltre possibile specificare l'azione da intraprendere quando l'analisi del codice rileva una violazione della regola.  
  
|Operazione|Descrizione|  
|------------|-----------------|  
|**Avviso**|Genera un avviso nel **elenco errori** finestra.|  
|**Erroree**|Genera un errore nel **elenco errori** finestra.|  
|**None**|Disabilita la regola.|  
  
 L'editor visualizza le regole in una struttura ad albero che set di gruppi di regole da una regola di campo specificato. Per aggiungere o rimuovere le regole da un set di regole, eseguire una o più delle seguenti operazioni:  
  
-   Selezionare o deselezionare la casella di controllo del nodo di gruppo per aggiungere o rimuovere tutte le regole nel gruppo. Quando si seleziona un gruppo, tutte le regole sono impostate le **avviso** azione.  
  
-   Fare clic su di **azione** campo di un gruppo, quindi specificare l'azione da applicare a tutte le regole nel gruppo.  
  
-   Selezionare o deselezionare la casella di controllo per una singola regola. Quando si seleziona la casella di controllo per una regola, la regola è impostata per l'azione di avviso.  
  
## <a name="rule-set-editor-toolbar"></a>Barra degli strumenti Editor Set di regole  
 È possibile utilizzare la barra degli strumenti dell'editor set di regole per raggruppare, filtrare e cercare i dati visualizzati nella griglia di set di regole.  
  
 Nella tabella seguente vengono descritti i controlli sulla barra degli strumenti dell'editor set di regole.  
  
|Controllo ToolBar|Descrizione|  
|---------------------|-----------------|  
|**Espandi tutto**|Vengono illustrate le regole in tutti i gruppi.|  
|**Comprimi tutto**|Nasconde le regole in tutti i gruppi.|  
|**Group By**|Specifica il campo da cui le regole sono raggruppate. Fare clic su  **\<None >** per mostrare le regole senza gruppi.|  
|**Opzioni colonne**|Specifica i campi della regola da visualizzare.|  
|**Nascondi le regole che non si applicano alla soluzione corrente**|Mostra o nasconde le regole che non sono dello stesso tipo di destinazione della soluzione.|  
|**Mostra regole che possono generare errori di analisi codice**|Mostra o nasconde le regole che vengono assegnate l'azione di errore.|  
|**Mostra regole che possono generare avvisi di analisi del codice**|Mostra o nasconde le regole che vengono assegnate l'azione di avviso.|  
|**Mostra regole non abilitate**|Mostra o nasconde le regole che vengono assegnate None azione.|  
|**Aggiungere o rimuovere set di regole figlio**|Aggiunge o rimuove le regole nei set di regole selezionato.|  
|**Regole di ricerca**|Cerca tutti i valori di campo per la stringa specificata.|  
  
## <a name="rule-set-fields"></a>Campi di Set di regole  
 Campi di visualizzazione di informazioni su una regola impostata e possono essere utilizzate per ordinare e raggruppare l'elenco delle regole di set di regole. Per visualizzare o nascondere i campi, fare clic su **Opzioni colonne** sulla regola barra degli strumenti e quindi selezionare o deselezionare le caselle di controllo dei campi per mostrare o nascondere.  
  
 Nella tabella seguente vengono descritti i campi di un set di regole.  
  
|Campo|Descrizione|  
|-----------|-----------------|  
|**ID**|Identificatore della regola.|  
|**Categoria**|Oltre all'appartenenza a set di regole, regole di analisi del codice vengono raggruppate per categoria. Per ulteriori informazioni, vedere [Code Analysis for Managed Code Warnings](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Il titolo della regola.|  
|**Spazio dei nomi**|Lo spazio dei nomi della regola.|  
|**Tipo di destinazione**|Indica se la regola per nativo, gestito o codice di database.|  
|**Azione**|L'azione eseguita quando la regola viene violata in un'esecuzione dell'analisi codice.<br /><br /> **Avviso** -genera un avviso.<br /><br /> **Errore** -genera un errore.<br /><br /> **Nessuna** -disabilita la regola.<br /><br /> È possibile modificare il campo dell'azione. Impostazione del valore su None è equivale a deselezionare la casella di controllo per la regola.|  
|**Set di regole di origine**|Il set di regole che contiene la regola.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Ordinamento e filtro dei set di regole  
 Dalle intestazioni di colonna della griglia di set di regole, è possibile ordinare e filtrare le regole in base ai valori del campo.  
  
-   Per ordinare gli elenchi di set di regole, fare clic sull'intestazione di colonna del campo da cui si desidera ordinare. Se il set di regole sono raggruppate, ogni gruppo viene ordinato singolarmente.  
  
-   Per filtrare i set di regole per il valore di un campo, fare clic sul pulsante filtro nell'intestazione di colonna del campo da cui si desidera filtrare. Selezionare le caselle di controllo dei valori di che si desidera visualizzare e deselezionare le caselle di controllo dei valori di che si desidera nascondere.