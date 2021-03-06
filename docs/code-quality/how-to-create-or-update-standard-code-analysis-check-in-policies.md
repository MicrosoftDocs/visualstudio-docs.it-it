---
title: Crea/aggiorna i criteri di archiviazione standard dell'analisi del codice
description: Informazioni su come assicurarsi che l'analisi del codice venga eseguita in tutti i progetti di codice in un progetto DevOps di Azure. Vedere come configurare i criteri di archiviazione dell'analisi del codice del progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d46ed89880c41cbcaa6982c386e2ff8f115f8de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860113"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice

È possibile richiedere l'esecuzione dell'analisi del codice in tutti i progetti di codice in un progetto DevOps di Azure usando i criteri di archiviazione dell'analisi del codice. La richiesta di analisi del codice può migliorare la qualità del codice archiviato nella codebase.

> [!NOTE]
> Questa funzionalità è disponibile solo se si usa Team Foundation Server.

I criteri di archiviazione dell'analisi del codice vengono impostati nelle impostazioni del progetto e si applicano a ogni progetto di codice. Le esecuzioni dell'analisi del codice sono configurate per i progetti di codice nel file di progetto (con estensione xxproj) per il progetto di codice. Le esecuzioni dell'analisi del codice vengono eseguite nel computer locale. Quando si Abilita un criterio di archiviazione dell'analisi del codice, i file in un progetto di codice da archiviare devono essere compilati dopo l'ultima modifica e un'esecuzione dell'analisi del codice che contiene almeno le regole nelle impostazioni del progetto devono essere eseguite nel computer in cui sono state apportate le modifiche.

- Per il codice gestito, è possibile impostare i criteri di archiviazione specificando un *set* di regole contenente un subset delle regole di analisi del codice.

- Per il codice C/C++, in Visual Studio 2017 versione 15,6 e precedenti, i criteri di archiviazione richiedono l'esecuzione di tutte le regole di analisi del codice. È possibile aggiungere direttive del pre-processore per disabilitare regole specifiche per i singoli progetti di codice nel progetto DevOps di Azure. In 15,7 e versioni successive è possibile usare **/analyze: RuleSet** per specificare le regole da eseguire. Per ulteriori informazioni, vedere [utilizzo di set di regole per specificare le regole C++ da eseguire](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

Dopo aver specificato i criteri di archiviazione per il codice gestito, i membri del team possono sincronizzare le impostazioni di analisi del codice per i progetti di codice nelle impostazioni dei criteri del progetto DevOps di Azure.

## <a name="to-open-the-check-in-policy-editor"></a>Per aprire l'editor dei criteri di archiviazione

1. In Team Explorer fare clic con il pulsante destro del mouse sul nome del progetto, scegliere **Impostazioni progetto**, quindi fare clic su **controllo del codice sorgente**.

1. Nella finestra di dialogo **controllo del codice sorgente** selezionare la scheda **criteri di archiviazione** .

1. Eseguire una delle operazioni seguenti:

    - Fare clic su **Aggiungi** per creare nuovi criteri di archiviazione.

    - Fare doppio clic sull'elemento di **analisi del codice** esistente nell'elenco tipo di **criteri** per modificare il criterio.

## <a name="to-set-policy-options"></a>Per impostare le opzioni dei criteri

Selezionare o deselezionare le opzioni seguenti:

|Opzione|Descrizione|
|------------|-----------------|
|**Applicare l'archiviazione per contenere solo i file che fanno parte della soluzione corrente.**|L'analisi del codice può essere eseguita solo su file specificati nei file di configurazione della soluzione e del progetto. Questo criterio garantisce che tutto il codice che fa parte di una soluzione venga analizzato.|
|**Applicare l'analisi codice C/C++ (/Analyze)**|Richiede che tutti i progetti C o C++ siano compilati con l'opzione del compilatore/analyze per eseguire l'analisi del codice prima di poterli archiviare.|
|**Imponi analisi codice per codice gestito**|Richiede che tutti i progetti gestiti eseguano l'analisi del codice e vengano compilati prima di poterli archiviare.|

## <a name="to-specify-a-managed-rule-set"></a>Per specificare un set di regole gestite

Dall'elenco **Esegui questo set di regole** , usare uno dei metodi seguenti:

- Selezionare un set di regole standard Microsoft.

- Selezionare un set di regole personalizzate facendo clic su **\<Select Rule Set from Source Control...>** . Digitare quindi il percorso del controllo della versione del set di regole nel browser del controllo del codice sorgente. La sintassi di un percorso di controllo della versione è la seguente:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Per ulteriori informazioni su come creare e implementare un set di regole dei criteri di archiviazione personalizzato, vedere [implementare criteri di archiviazione personalizzati per il codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vedi anche

- [Implementare i criteri di archiviazione di analisi codice personalizzati per il codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
