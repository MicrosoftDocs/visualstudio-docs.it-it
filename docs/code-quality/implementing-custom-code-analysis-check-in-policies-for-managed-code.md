---
title: Implementazione di criteri di controllo analisi codice personalizzati per codice gestito in Visual Studio
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c50daf82a5dc5774cae75ecab54f1455c1a1c251
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementare criteri di controllo dell'analisi del codice personalizzato per il codice gestito

Analisi del codice dei criteri di archiviazione specificano un set di regole che i membri di un progetto team devono eseguire sul codice sorgente prima che venga verificata controllo della versione. Microsoft fornisce un set di standard *set di regole* tale analisi del codice del gruppo di regole in aree funzionali. *Set di regole di criteri di controllo personalizzati* specificare un set di regole di analisi del codice che sono specifiche per un progetto team. Un set di regole viene archiviato in un file con estensione ruleset.

Criteri di archiviazione vengono impostati a livello di progetto team e specificati dal percorso di un file con estensione ruleset nella struttura di controllo della versione. Non sono previste restrizioni sul percorso di controllo della versione del set di regole personalizzato criteri del team.

Analisi del codice è configurato per singoli progetti di codice nella finestra proprietà per ogni progetto. Una regola personalizzata impostata per un progetto di codice viene specificata dalla posizione fisica del file con estensione ruleset nel computer locale. Quando viene specificato un file con estensione ruleset che si trova nella stessa unità del progetto di codice, Visual Studio Usa un percorso relativo per il file di configurazione del progetto.

Una pratica consigliata per la creazione di un set di regole personalizzate del progetto team consiste nell'archiviare i file con estensione ruleset dei criteri di archiviazione in una cartella speciale che non fa parte di qualsiasi progetto di codice. Se si archivia il file in una cartella dedicata, è possibile applicare le autorizzazioni che limitano che è possono modificare il file di regole ed è possibile spostare facilmente la struttura di directory che contiene il progetto in un'altra directory o computer.

## <a name="create-the-team-project-custom-check-in-rule-set"></a>Creare il Set di regole di controllo personalizzato di progetti Team

Per creare una regola personalizzata impostata per un progetto team, si crea una cartella speciale per i criteri di controllo set di regole in **Esplora controllo codice sorgente**. È quindi possibile creare il file del set di regole e aggiungere il file al controllo della versione. Infine, specificare il set di regole come il codice check-in Criteri di analisi per il progetto team.

> [!NOTE]
> Per creare una cartella in un progetto team, è necessario mappare la radice del progetto team in un percorso nel computer locale.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Per creare la cartella controllo della versione per il set di regole di criteri di archiviazione

1. In Team Explorer, espandere il nodo del progetto team e quindi fare clic su **controllo del codice sorgente**.

2. Nel **cartelle** riquadro, fare clic sul progetto team e quindi fare clic su **nuova cartella**.

3. Nel riquadro principale di controllo del codice sorgente, fare doppio clic su **nuova cartella**, fare clic su **rinominare**e digitare un nome per il set di regole cartella.

### <a name="to-create-the-check-in-policy-rule-set"></a>Per creare il set di regole di criteri di archiviazione

1. Nel **File** dal menu **New**, quindi fare clic su **File**.

2. Nel **categorie** elenco, fare clic su **generale**.

3. Nel **modelli** fare doppio clic su **Set di regole di analisi codice**.

4. [Specificare le regole](../code-quality/how-to-create-a-custom-rule-set.md) da includere nel set di regole e quindi salvare la regola impostare file nella cartella set di regole creato.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Per aggiungere la regola impostare file al controllo della versione

1. In **Esplora controllo codice sorgente**, fare doppio clic su nuova cartella e quindi fare clic su **Aggiungi elementi alla cartella**.

     Per ulteriori informazioni, vedere [Git e VSTS](/vsts/git/overview).

2. Scegliere il set di regole file creato e quindi fare clic su **fine**.

     Il file viene aggiunto al controllo del codice sorgente ed estratto.

3. Nel **Esplora controllo codice sorgente** finestra Dettagli, fare doppio clic sul nome del file e quindi fare clic su **archiviare modifiche in sospeso**.

4. Nel **archiviazione** nella finestra di dialogo è possibile aggiungere un commento e quindi fare clic su **Archivia**.

    > [!NOTE]
    > Se è stato già configurato un criterio di controllo dell'analisi codice per il progetto team e si è scelto di **Consenti archiviazione dei soli file che fanno parte della soluzione corrente**, verrà generato un avviso di errore dei criteri. Nella finestra di dialogo Errore criteri selezionare **Ignora errore criteri e continua archiviazione**. Aggiungere un commento obbligatorio e quindi fare clic su **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Per specificare la regola di set di file come i criteri di controllo

1. Nel **Team** dal menu **impostazioni progetto Team**, quindi fare clic su **controllo del codice sorgente**.

2. Fare clic su **criteri di archiviazione**, quindi fare clic su **Aggiungi**.

3. Nel **criteri di archiviazione** fare doppio clic su **analisi del codice**e assicurarsi che il **Attiva analisi codice per il codice gestito** casella di controllo è selezionata.

4. Nel **eseguire il set di regole** elenco, fare clic su  **\<seleziona Set di regole dal controllo del codice sorgente >**.

5. Digitare il percorso del file di set di regole dei criteri di archiviazione nel controllo della versione.

     Il percorso deve essere conforme alla sintassi seguente:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > È possibile copiare il percorso tramite una delle seguenti procedure in **Esplora controllo codice sorgente**:

    - Nel **cartelle** riquadro, fare clic sulla cartella che contiene il file del set di regole. Copiare il percorso della cartella in cui viene visualizzato nel controllo della versione di **origine** , quindi digitare il nome del file del set di regole manualmente.

    - Nella finestra dei dettagli, fare doppio clic su file del set di regole e quindi fare clic su **proprietà**. Nel **generale** scheda, copiare il valore in **nome Server**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizzare i progetti di codice per il Set di regole dei criteri di archiviazione

Specificare una regola di criteri di archiviazione di progetti team impostato come il set di regole di analisi codice di una configurazione di progetto di codice nella finestra di dialogo proprietà del progetto di codice. Se il set di regole si trova nella stessa unità del progetto di codice, viene utilizzato un percorso relativo per specificare i set di regole se il percorso è selezionato nella finestra di dialogo file. Strutture di controllo Abilita il percorso relativo le proprietà del progetto sia portabile in altri computer che utilizzano una versione locale simile.

### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Per specificare una regola di progetto team impostata come set di regole di un progetto di codice

1. Se necessario, è possibile recuperare la cartella set di regole dei criteri di archiviazione e un file dal controllo della versione.

   È possibile eseguire questo passaggio in **Esplora controllo codice sorgente** facendo clic con il set di regole cartella e quindi fare clic su **Leggi ultima versione**.

2. In **Esplora**, fare clic sul progetto codice e quindi fare clic su **proprietà**.

3. **Fare clic su analisi del codice**.

4. Se necessario, selezionare le opzioni appropriate nel **configurazione** e **piattaforma** Elenca.

5. Per eseguire l'analisi codice ogni volta che il progetto di codice viene compilato utilizzando la configurazione specificata, selezionare il **Attiva analisi codice in fase di compilazione (definisce la costante CODE_ANALYSIS)** casella di controllo.

6. Per ignorare codice nei componenti di altre società, selezionare il **Elimina i risultati dal codice generato** casella di controllo.

7. Nel **eseguire il set di regole** elenco, fare clic su  **\<Sfoglia... >**.

8. Specificare la versione locale del file di set di regole dei criteri di archiviazione.