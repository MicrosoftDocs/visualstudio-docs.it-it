---
title: "Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb0642828daa96d7904d4e4bb967afc5f1c563d9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice

È possibile richiedere che l'analisi del codice deve essere eseguito in tutti i progetti di codice in un progetto team usando i criteri di controllo dell'analisi codice. Richiedere l'analisi del codice, è possibile migliorare la qualità del codice che viene archiviato nella codebase.

> [!NOTE]
> Questa funzionalità è disponibile solo se si utilizza Team Foundation Server.

Criteri di controllo dell'analisi del codice vengono impostati nelle impostazioni del progetto team e si applicano a ogni progetto di codice nel progetto team. Esecuzioni dell'analisi del codice sono configurate per i progetti di codice nel file di progetto (con estensione xxproj) per il progetto di codice. Esecuzioni dell'analisi del codice vengono eseguite nel computer locale. Quando si abilita un criterio di controllo dell'analisi codice, devono essere compilati in un progetto di codice che devono essere archiviati file termine dell'ultima modifica e l'analisi del codice esegue che contiene, come minimo, le regole nelle impostazioni del progetto team devono essere eseguite nel computer in cui il c sono state apportate le revisioni.

- Per codice gestito, si impostano i criteri di archiviazione specificando un *set di regole* che contiene un subset delle regole di analisi codice.

- Per il codice C/C++, i criteri di controllo richiedono che tutte le regole di analisi di codice vengono eseguite. È possibile aggiungere le direttive del preprocessore per disabilitare regole specifiche per singoli progetti di codice nel progetto team.

Dopo aver specificato un criterio di controllo per il codice gestito, i membri del team possono sincronizzare le impostazioni di analisi codice per i progetti di codice alle impostazioni dei criteri del progetto team.

### <a name="to-open-the-check-in-policy-editor"></a>Per aprire l'editor Criteri di archiviazione

1. In Team Explorer, fare clic sul nome del progetto team, scegliere **impostazioni progetto Team**, quindi fare clic su **controllo del codice sorgente**.

1. Nel **controllo del codice sorgente** la finestra di dialogo, seleziona il **criteri di archiviazione** scheda.

1. Eseguire una delle operazioni seguenti:

    - Fare clic su **Aggiungi** per creare un nuovo criterio di controllo.

    - Fare doppio clic su esistente **analisi del codice** elemento il **tipo di criteri** elenco per modificare i criteri.

### <a name="to-set-policy-options"></a>Per impostare le opzioni dei criteri

Selezionare o deselezionare le opzioni seguenti:

    |Opzione|Descrizione|
    |------------|-----------------|
    |**Consenti archiviazione dei soli file che fanno parte della soluzione corrente.**|Analisi del codice è possibile eseguire solo sui file specificati nel file di configurazione di soluzione e progetto. Questo criterio assicura che tutto il codice che fa parte di una soluzione viene analizzato.|
    |**Applicare l'analisi del codice C/C++ (/analyze)**|Richiede che tutti i progetti C o C++ generati con la / analizzare l'opzione del compilatore per eseguire l'analisi del codice prima che possano essere archiviati.|
    |**Applicare l'analisi del codice per il codice gestito**|Richiede che tutti i progetti gestiti, eseguire l'analisi del codice e compilare prima che possano essere archiviati.|

### <a name="to-specify-a-managed-rule-set"></a>Per specificare un set di regole gestito

- Dal **eseguire il set di regole** elenco, utilizzare uno dei metodi seguenti:

    - Selezionare un set di regole standard Microsoft.

    - Per selezionare un set di regole personalizzato, fare clic su  **\<seleziona Set di regole dal controllo del codice sorgente... >**, quindi digitare il percorso del controllo della versione del set di regole nel browser di controllo del codice sorgente. La sintassi di un percorso di controllo della versione è:

    - **$/** `TeamProjectName` **/** `VersionControlPath`

    - Per ulteriori informazioni su come creare e implementare una regola dei criteri di controllo personalizzato, vedere [criteri di controllo che implementa personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vedere anche

[Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)