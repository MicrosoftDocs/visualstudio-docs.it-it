---
title: "Procedura: abilitare e disabilitare l'analisi della soluzione completa per il codice gestito"
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 52b181fe58297bb10e1a2abd0f9ff7bf9c78069e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: abilitare e disabilitare l'analisi della soluzione completa per il codice gestito

*Analisi della soluzione completa* è una funzionalità di Visual Studio che consente di visualizzare i problemi di analisi del codice solo nel file aperti in Visual c# o Visual Basic nella soluzione, o anche nel codice i file che vengono chiusi. Per impostazione predefinita, analisi della soluzione completa viene *abilitata* per Visual Basic, e *disabilitato* per Visual c#.

Può essere utile visualizzare tutti i problemi in tutti i file, ma può anche essere distrazione. Rallenta Visual Studio se la soluzione è molto grande o dispone di molti file. Per limitare il numero di problemi illustrato e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi della soluzione completa. Se necessario, è possibile riabilitare facilmente questa funzionalità.

## <a name="to-toggle-full-solution-analysis"></a>Per attivare o disattivare analisi della soluzione completa

1. Per aprire la **opzioni** la finestra di dialogo, nella barra dei menu in Visual Studio scegliere **strumenti** > **opzioni**.

1. Nel **opzioni** finestra di dialogo scegliere **Editor di testo** > **c#** o **base**  >   **Advanced**.

1. Selezionare il **abilitare l'analisi della soluzione completa** casella di controllo per abilitare l'analisi della soluzione completa, o deselezionare la casella per disabilitarla. Scegliere **OK** al termine.

    ![Abilitare la casella di controllo analisi soluzione completa.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Risultati di abilitazione e disabilitazione di analisi della soluzione completa

Nella schermata seguente, è possibile visualizzare i risultati quando sono abilitata l'analisi della soluzione completa. Tutti gli errori e problemi di analisi del codice in *tutti* dei file nella soluzione vengono visualizzati, anche se i file sono aperti.

![Analisi della soluzione completa abilitata.](../code-quality/media/fsa_enabled.png)

Nella schermata seguente mostra i risultati dalla stessa soluzione dopo la disabilitazione di analisi della soluzione completa. Vengono visualizzati solo gli errori e problemi di analisi del codice nei file di soluzione aperta nel **elenco errori**.

![Analisi della soluzione completa disabilitato.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Disabilitare automaticamente l'analisi della soluzione completa

Se Visual Studio rileva che 200 MB o minore di memoria di sistema disponibile per il processo è disabilita automaticamente analisi della soluzione completa (e alcune altre funzionalità) se è abilitato. In questo caso, viene visualizzato un avviso che informa che Visual Studio è disabilitato alcune funzionalità. Un pulsante consente di riattivare analisi della soluzione completa, se si desidera.

![Testo dell'avviso la sospensione di analisi della soluzione completa](../code-quality/media/fsa_alert.png)