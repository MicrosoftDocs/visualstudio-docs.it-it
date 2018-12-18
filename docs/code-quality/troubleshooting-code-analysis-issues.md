---
title: Risoluzione dei problemi di analisi codice
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9029c7be21fe02b9d6b1c4436658df74eb3c37f9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-code-analysis-issues"></a>Risoluzione dei problemi di analisi codice
L'argomento contiene informazioni sulla risoluzione dei problemi seguenti relativi all'analisi del codice di Visual Studio.

-   [Le modifiche apportate a un set di regole di Visual Studio 2010 non si riflettono nelle versioni precedenti di Visual Studio](#ChildRuleSetChangesInPreviousVersions)

##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Le modifiche apportate a un set di regole di Visual Studio 2010 non si riflettono nelle versioni precedenti di Visual Studio
 Quando si crea un set di regole in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] che contiene un set di regole figlio, è possibile che una modifica al set di regole figlio non venga applicata nelle esecuzioni dell'analisi del codice nei computer che usano una versione precedente di Visual Studio. Per risolvere questo problema, è necessario forzare una riscrittura del set di regole padre, ovvero del set di regole che contiene il set di regole figlio.

1.  Aprire il set di regole padre in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].

2.  Apportare una modifica, ad esempio aggiungere o eliminare una regola, e salvare il set di regole.

3.  Riaprire il set di regole, annullare la modifica e salvare nuovamente il set di regole.

## <a name="see-also"></a>Vedere anche
 [Analisi della qualità dell'applicazione](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) [analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [mediante regola imposta per raggruppare regole di analisi codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)