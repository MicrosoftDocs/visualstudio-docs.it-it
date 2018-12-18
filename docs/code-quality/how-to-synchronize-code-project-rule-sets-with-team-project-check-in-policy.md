---
title: 'Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bb6f97495eec73e52751f79d92e2f078bd13b24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team

Sincronizzare le impostazioni di analisi codice per i progetti di codice per i criteri di controllo per il progetto team specificando un set di regole che contiene almeno le regole che vengono specificate nel set di regole per i criteri di controllo. Sviluppatore responsabile può informare è il nome e la posizione del set di regole per i criteri di controllo. È possibile utilizzare una delle opzioni seguenti per assicurarsi che l'analisi del codice per il progetto utilizza il set corretto di regole:

-   Se i criteri di controllo utilizzano uno dei set di regole predefinite Microsoft, aprire la finestra di dialogo proprietà per il progetto di codice, visualizzare la pagina di analisi del codice e selezionare la regola impostata nella pagina dell'analisi del codice delle impostazioni di progetto di codice. Il set di regole standard installate automaticamente con Visual Studio di Microsoft sono impostati sola lettura e non deve essere modificato. Se non vengono modificati i set di regole, le regole nel set di regole locali e criteri di corrispondenza è garantite.

-   Se i criteri di controllo utilizzano un set di regole personalizzate, eseguire un'operazione get sul file di set di regole nel controllo della versione per creare una copia locale. Quindi specificare il percorso locale nelle impostazioni di analisi del codice per il progetto di codice. Le regole sono garantite per la corrispondenza se il set di regole per i criteri di archiviazione sono aggiornata.

     Se si esegue il mapping del percorso di controllo della versione in una cartella locale in relazione stessa radice del progetto team come progetto di codice, il percorso della regola viene impostato utilizzando un percorso relativo. Il percorso relativo assicura che l'impostazione di progetto di codice per l'analisi del codice può essere spostato in altri computer.

-   Personalizzare una copia del set di regole per i criteri di controllo per un progetto di codice. Assicurarsi che il nuovo set di regole contiene tutte le regole nei criteri di archiviazione e altre regole che si desiderano includere. È necessario assicurarsi che il set di regole include tutte le regole nel set di regole per i criteri di controllo.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Per specificare una regola standard Microsoft set

1.  In **Esplora**, fare clic sul progetto codice e quindi fare clic su **proprietà**.

2.  Fare clic su **l'analisi del codice**.

3.  Nel **eseguire il set di regole** elenco, fare clic su set di regole dei criteri di archiviazione.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Per specificare un set di regole di criteri di archiviazione personalizzate

1.  Se necessario, eseguire un'operazione get sul file di set di regole che specifica i criteri di controllo.

2.  In **Esplora**, fare clic sul progetto codice e quindi fare clic su **proprietà**.

3.  Fare clic su **l'analisi del codice**.

4.  Nel **eseguire il set di regole** elenco, fare clic su  **\<Sfoglia... >**.

5.  Nel **aprire** finestra di dialogo, specificare i file del set di regole dei criteri di controllo.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Per creare una regola personalizzata impostata per un progetto di codice

1.  Seguire una delle procedure in questo argomento per selezionare i criteri di archiviazione del progetto team nella pagina dell'analisi del codice della finestra di dialogo Impostazioni di progetto.

2.  Fare clic su **aprire**.

3.  Aggiungere o rimuovere le regole usando il [editor set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4.  Salvare la regola modificata impostato su un file con estensione ruleset nel computer locale o in un percorso UNC.

5.  Aprire la finestra di dialogo proprietà per il progetto di codice e visualizzare il **analisi del codice** pagina.

6.  Nel **eseguire il set di regole** elenco, fare clic su  **\<Sfoglia... >**.

7.  Nel **aprire** finestra di dialogo, specificare il set di regole file.