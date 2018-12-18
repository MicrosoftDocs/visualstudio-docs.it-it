---
title: "Procedura: specificare il set di regole di codice gestito per più progetti in una soluzione | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e0b6a2864340f87702b765f49605ebdb3aaa555c
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Procedura: specificare set di regole di codice gestito per più progetti in una soluzione

Per impostazione predefinita, tutti i progetti gestiti, di una soluzione vengono assegnati l'analisi del codice di regole minime consigliate Microsoft *set di regole*. È possibile modificare i set di regole che vengono assegnati ai progetti di una soluzione nella finestra di dialogo proprietà per la soluzione.

> [!NOTE]
> Per impostazione predefinita, l'analisi del codice di progetto non viene eseguita come un'istruzione di compilazione. Per abilitare l'analisi del codice come un'istruzione di compilazione, vedere [come: Configura analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

1. Aprire la soluzione in Visual Studio.

2. Nel **Analizza** menu, fare clic su **Configura analisi codice per soluzioni**.

3. Se necessario, espandere **proprietà comuni**, quindi fare clic su **le impostazioni dell'analisi codice**.

4. È possibile specificare una set di regole per uno o più progetti.

    - Per specificare una set di regole per un singolo progetto, fare clic sul nome del progetto.

    - Per specificare una set di regole per più progetti, tenere premuto CTRL e fare clic sul nome del progetto.

    - Per specificare tutti i progetti nella soluzione, tenere premuto MAIUSC e fare clic nell'elenco di progetto.

5. Fare clic su di **del Set di regole** campo di un progetto e quindi scegliere il nome della regola set che si desidera applicare.