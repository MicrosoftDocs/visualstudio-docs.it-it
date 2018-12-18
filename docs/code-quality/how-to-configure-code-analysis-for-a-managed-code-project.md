---
title: Configurare l'analisi del codice in Visual Studio
ms.date: 04/04/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 66faf26170e1e102ccbaffcb74334bdd20e4d8ae
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procedura: Configurare l'analisi codice per un progetto di codice gestito

In Visual Studio, è possibile scegliere da un elenco di analisi del codice *set di regole* da applicare a un progetto di codice gestito. Il set di regole predefinito è *regole minime consigliate Microsoft*. È possibile applicare un altro set di regole a un progetto o a tutti i progetti in una soluzione.

> [!TIP]
> Per informazioni su come configurare una set di regole per le applicazioni Web ASP.NET, vedere [come: Configura analisi codice per un'applicazione Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Per configurare una set di regole per un progetto .NET Framework

1. Aprire la **analisi del codice** scheda nelle pagine delle proprietà del progetto. È possibile farlo in uno dei modi seguenti:

   - In **Esplora soluzioni**, selezionare il progetto. Nella barra dei menu, selezionare **Analizza** > **Configura analisi codice** > **per \<projectname >**.

   - Fare clic sul progetto in **Esplora soluzioni** e selezionare **delle proprietà**e quindi selezionare il **analisi del codice** scheda.

1. Nel **Configuration** e **piattaforma** gli elenchi, selezionare la piattaforma di destinazione e configurazione di compilazione.

1. Per eseguire l'analisi codice ogni volta che il progetto viene compilato con la configurazione selezionata, selezionare il **Attiva analisi codice in fase di compilazione** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice selezionando **Analizza** > **Esegui analisi del codice** > **Esegui analisi del codice su \<projectname >**.

1. Per impostazione predefinita, l'analisi del codice non segnala gli avvisi del codice generato automaticamente da strumenti esterni. Per visualizzare gli avvisi del codice generato, deselezionare il **Elimina i risultati dal codice generato** casella di controllo.

    > [!NOTE]
    > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un form o un modello, senza che venga sovrascritto.

1. Nel **eseguire il set di regole** elenco, effettuare una delle operazioni seguenti:

    - Selezionare il set di regole che si desidera utilizzare.

    - Selezionare  **\<Sfoglia... >** per trovare una regola personalizzata esistente impostato che non è presente nell'elenco.

    - Definire un [set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Specificare il set di regole per più progetti in una soluzione

Per impostazione predefinita, tutti i progetti gestiti di una soluzione viene assegnato il *regole minime consigliate Microsoft* set di regole di analisi del codice. È possibile modificare i set di regole che vengono assegnati ai progetti di una soluzione nel **proprietà** finestra di dialogo per la soluzione.

1. Aprire la soluzione in Visual Studio.

2. Nel **Analizza** dal menu **Configura analisi codice per soluzioni**.

3. Se necessario, espandere **proprietà comuni**, quindi selezionare **le impostazioni dell'analisi codice**.

4. È possibile specificare una set di regole per uno o più progetti:

    - Per specificare una set di regole per un singolo progetto, selezionare il nome del progetto.

    - Per specificare una set di regole per più progetti, tenere premuto **Ctrl** e selezionare i nomi dei progetti.

    - Per specificare tutti i progetti nella soluzione, tieni premuto **MAIUSC** e fare clic su nell'elenco di progetto.

5. Selezionare il **del Set di regole** campo di un progetto e quindi selezionare il nome della regola impostata che si desidera applicare.

## <a name="see-also"></a>Vedere anche

- [Procedura: Configurare l'analisi del codice per un'applicazione Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)