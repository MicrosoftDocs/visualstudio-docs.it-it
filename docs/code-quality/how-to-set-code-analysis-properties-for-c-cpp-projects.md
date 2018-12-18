---
title: 'Procedura: impostare le proprietà di analisi del codice per progetti C/C++'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: d072d6c00ad59d886fb713c2ac98886524371031
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Procedura: impostare le proprietà di analisi del codice per progetti C/C++
È possibile configurare le regole che utilizza lo strumento di analisi codice per analizzare il codice in ogni configurazione del progetto. Inoltre, è possibile indirizzare l'analisi del codice per l'esclusione di avvisi da codice che è stato generato e aggiunto al progetto da uno strumento di terze parti.

## <a name="code-analysis-property-page"></a>Pagina delle proprietà analisi codice
 Il **analisi del codice** pagina delle proprietà contiene tutte le impostazioni di configurazione di analisi di codice per un progetto. Per aprire la pagina proprietà di analisi codice per un progetto in **Esplora**, fare clic sul progetto e quindi fare clic su **proprietà**. Espandere quindi **le proprietà di configurazione** e selezionare il **analisi del codice** scheda.

## <a name="project-configuration-and-platform"></a>Piattaforma e configurazione di progetto
 Il **configurazione** elenco e **piattaforma** elenco consente di applicare le impostazioni dell'analisi codice diverse combinazioni di piattaforma e configurazione di progetto diverso. Ad esempio, è possibile indirizzare compilazioni di analisi del codice per applicare un set di regole per il progetto per il debug e genera un set diverso per il rilascio.

## <a name="enabling-code-analysis"></a>Attivazione dell'analisi del codice
 È possibile decidere se abilitare l'analisi del codice per il progetto selezionando **Abilita analisi codice per C/C++ in fase di compilazione**. In combinazione con il **configurazione** elenco, è possibile, ad esempio, decidere di disabilitare l'analisi del codice per le compilazioni di debug e attiva per versione build.

 Se il progetto contiene codice gestito, è possibile decidere se abilitare o disabilitare l'analisi del codice selezionando **Attiva analisi codice in fase di compilazione**.

 Analisi del codice è progettato per migliorare la qualità del codice e di evitare trappole comuni. Pertanto, valutare attentamente se si desidera disabilitare l'analisi del codice. In genere è preferibile disabilitare i set di regole o regole singole che non si desidera applicare al progetto.

## <a name="generated-code"></a>Codice generato
 Gli sviluppatori spesso utilizzano strumenti che consentono di sviluppare rapidamente applicazioni. Questi strumenti possono generare codice che viene aggiunto al progetto. Si potrebbe voler visualizzare le violazioni delle regole individuate dall'analisi nel codice generato. Tuttavia, si potrebbe non si desidera visualizzarli se non si desidera mantenere il codice.

 Il **non visualizzare i risultati dal codice generato** casella di controllo di **generale** pagina delle proprietà consente di specificare se si desidera visualizzare gli avvisi di analisi codice da codice gestito che viene generato da uno strumento di terze parti .

## <a name="rule-sets"></a>Set di regole
 Se il progetto contiene codice gestito, è possibile selezionare le regole da applicare nell'analisi del codice tramite la selezione di una set di regole dal **eseguire il set di regole** elenco.

## <a name="see-also"></a>Vedere anche
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [l'analisi del codice per avvisi C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)