---
title: Refactoring del codice Python in Visual Studio | Microsoft Docs
description: Come eseguire facilmente il refactoring di codice Python in Visual Studio tramite ridenominazione degli identificatori, estrazione dei metodi, aggiunta delle importazioni e rimozione delle importazioni inutilizzate.
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: a89a659731e85b61aa60a522c27278868e60170c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="refactoring-python-code"></a>Refactoring del codice Python

Visual Studio offre diversi comandi per la trasformazione e la pulizia automatiche del codice sorgente Python:

- [Rinomina](#rename) consente di modificare un nome di classe, metodo o variabile selezionato
- [Estrai metodo](#extract-method) consente di creare un nuovo metodo dal codice selezionato
- [Aggiungi importazione](#add-import) fornisce uno smart tag per aggiungere un'importazione mancante
- [Rimuovi importazioni](#remove-unused-imports) consente di rimuovere le importazioni inutilizzate

<a name="rename-variable"</a>

## <a name="rename"></a>Rinomina

1. Fare clic con il pulsante destro del mouse sull'identificatore che si vuole rinominare e scegliere **Rinomina** oppure posizionare il cursore su tale identificatore e scegliere i comandi **Modifica > Refactoring > Rinomina** (F2).
1. Nella finestra di dialogo **Rinomina** visualizzata immettere il nuovo nome per l'identificatore e selezionare **OK**:

  ![Richiesta del nuovo nome di identificatore per la ridenominazione](media/code-refactor-rename-1.png)

1. Nella finestra di dialogo successiva selezionare i file e le istanze nel codice a cui applicare la ridenominazione. Selezionare qualsiasi istanza singola per visualizzare in anteprima la modifica specifica:

  ![Selezione delle posizioni in cui applicare le modifiche nella finestra di dialogo Rinomina](media/code-refactor-rename-2.png)

1. Selezionare **Applica** per apportare le modifiche nei file di codice sorgente. Questa azione può essere annullata.

## <a name="extract-method"></a>Estrai metodo

1. Selezionare le righe di codice o l'espressione da estrarre in un metodo separato.
1. Selezionare i comandi di menu **Modifica > Effettua refactoring > Estrai metodo** oppure digitare CTRL-R,M.
1. Nella finestra di dialogo visualizzata immettere un nuovo nome di metodo, indicare la posizione in cui estrarlo e selezionare eventuali variabili di chiusura. Le variabili non selezionate per la chiusura vengono trasformate in argomenti del metodo:

  ![Finestra di dialogo Estrai metodo](media/code-refactor-extract-method-1.png)

1. Selezionare **OK** e il codice verrà modificato di conseguenza:

  ![Effetto dell'estrazione di un metodo](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Aggiungi importazione

Quando si posiziona il cursore su un identificatore per cui mancano le informazioni sul tipo, Visual Studio offre uno smart tag, ovvero l'icona a forma di lampadina a sinistra del codice, i cui comandi consentono di aggiungere l'istruzione `import` o `from ... import` necessaria:

![Smart tag Aggiungi importazione](media/code-refactor-add-import-1.png)

Visual Studio offre la funzione di completamento di `import` per i pacchetti e i moduli di primo livello nel progetto corrente e nella libreria standard. Visual Studio offre anche la funzione di completamento di `from ... import` per moduli e pacchetti secondari, oltre che per membri di modulo. I completamenti includono funzioni, classi o dati esportati. Selezionando una delle due opzioni, l'istruzione viene aggiunta all'inizio del file dopo le altre importazioni oppure in un'istruzione `from ... import` esistente se lo stesso modulo è già importato.

![Risultato dell'aggiunta di un'importazione](media/code-refactor-add-import-2.png)

Visual Studio tenta di escludere i membri che non sono effettivamente definiti in un modulo, ad esempio i moduli importati in un altro, ma che non sono elementi figlio del modulo che effettua l'importazione. Ad esempio, molti moduli usano `import sys` invece di `from xyz import sys`, quindi il completamento dell'importazione di `sys` da altri moduli non è visibile, anche se per i moduli manca un membro `__all__` che esclude `sys`.

Analogamente, Visual Studio filtra le funzioni importate da altri moduli o dallo spazio dei nomi predefinito. Ad esempio, se un modulo importa la funzione `settrace` dal modulo `sys`, in teoria potrebbe essere possibile importarlo da tale modulo. È però preferibile usare `import settrace from sys` direttamente, quindi Visual Studio offre specificamente tale istruzione.

Infine, Visual Studio esclude l'importazione se un elemento viene normalmente escluso, ma ha altri valori che verrebbero inclusi, ad esempio perché al nome è stato assegnato un valore nel modulo. Questo comportamento presuppone che il valore non debba essere esportato perché è definito in un altro modulo ed è pertanto probabile che l'assegnazione aggiuntiva sia un valore fittizio, anch'esso non esportato.

<a name="remove-imports"</a>

## <a name="remove-unused-imports"></a>Rimuovi importazioni

Durante la scrittura del codice è facile ritrovarsi con istruzioni `import` per moduli che non vengono usati affatto. Dato che Visual Studio analizza il codice, può determinare automaticamente se un'istruzione `import` è necessaria verificando se il nome importato viene usato nell'ambito dell'istruzione.

Fare clic con il pulsante destro del mouse in qualsiasi punto dell'editor e scegliere **Rimuovi importazioni**, quindi scegliere l'opzione per l'ambito da cui eseguire la rimozione, ovvero **Tutti gli ambiti** o **Ambito corrente**:

![Menu Rimuovi importazioni](media/code-refactor-remove-imports-1.png)

Visual Studio apporterà quindi le modifiche appropriate al codice:

![Effetto della rimozione delle importazioni](media/code-refactor-remove-imports-2.png)

Si noti che Visual Studio non tiene conto del flusso di controllo. L'uso di un nome prima di un'istruzione `import` viene interpretato come uso effettivo del nome. Visual Studio ignora anche tutte le importazioni `from __future__`, le importazioni che vengono eseguite all'interno di una definizione di classe, nonché da istruzioni `from ... import *`.