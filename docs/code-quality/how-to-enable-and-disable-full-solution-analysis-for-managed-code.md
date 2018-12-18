---
title: 'Procedura: abilitare e disabilitare l''analisi della soluzione completa per il codice gestito | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: abilitare e disabilitare l'analisi della soluzione completa per il codice gestito

*Analisi della soluzione completa* è una funzionalità di Visual Studio che consente di visualizzare i problemi di analisi del codice solo in un file aperti in Visual c# o Visual Basic nella soluzione, o anche nel codice i file vengono chiusi. Per impostazione predefinita, l'analisi della soluzione completa sono abilitato per Visual Basic e disabilitato per Visual c#.

Mentre la possibilità di visualizzare tutti i problemi in tutti i file è utile, può essere fonte di distrazione. Si può anche lenta Visual Studio verso il basso se la soluzione è molto grande o dispone di molti file. Per limitare il numero di problemi illustrato e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi della soluzione completa. Se necessario, è possibile riabilitare facilmente questa funzionalità.

## <a name="to-toggle-full-solution-analysis"></a>Per attivare o disattivare analisi della soluzione completa

1. Per aprire la **opzioni** la finestra di dialogo, nella barra dei menu in Visual Studio scegliere **strumenti** > **opzioni**.

1. Nel **opzioni** finestra di dialogo scegliere **Editor di testo** > **c#** o **base**  >  ** Advanced**.

1. Selezionare il **abilitare l'analisi della soluzione completa** casella di controllo per abilitare l'analisi della soluzione completa, o deselezionare la casella per disabilitarla. Scegliere il **OK** pulsante una volta terminato.

    ![Abilitare la casella di controllo di analisi soluzione completa. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Risultati di abilitazione e disabilitazione di analisi della soluzione completa

Nella schermata seguente, è possibile visualizzare i risultati quando sono abilitata l'analisi della soluzione completa. Tutti gli errori e problemi di analisi del codice in *tutti* dei file nella soluzione vengono visualizzati, anche se i file sono aperti.

![Analisi della soluzione completa abilitata. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

Nella schermata seguente mostra i risultati dalla stessa soluzione dopo la disabilitazione di analisi della soluzione completa. Solo gli errori e problemi di analisi del codice in aprono Esplora file vengono visualizzati nell'elenco errori.

![Analisi della soluzione completa disabilitato. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Disattiva automaticamente l'analisi della soluzione completa

Se Visual Studio rileva che 200MB o minore di memoria di sistema è disponibile, disabilita automaticamente analisi della soluzione completa (così come altre caratteristiche) se è abilitato. In questo caso, viene visualizzato un avviso che informa dell'oggetto. Un pulsante consente di abilitare nuovamente l'analisi della soluzione completa se lo si desidera.

![Avviso di analisi della soluzione completa di sospensione](../code-quality/media/fsa_alert.png "FSA_Alert")