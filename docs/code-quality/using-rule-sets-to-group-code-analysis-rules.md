---
title: Regola di utilizzo di set per raggruppare regole di analisi codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 265ca57904cb47c52ecaf6ba260e726da9b8a063
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2018
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Utilizzo di set di regole per raggruppare regole di analisi del codice

Quando si configura l'analisi del codice in Visual Studio, è possibile scegliere da un elenco di predefinite Microsoft *set di regole*. Un set di regole è un raggruppamento logico di regole di analisi del codice che identificano i problemi di destinazione e specifiche condizioni. Ad esempio, è possibile applicare un set di regole è progettato per l'analisi codice per le API disponibile pubblicamente oppure è possibile applicare un set di regole che include solo le regole minime consigliate. È inoltre possibile applicare un set di regole che include tutte le regole.

È possibile personalizzare una set di regole mediante l'aggiunta o eliminazione di regole, o modificando le regole siano visibili nel **elenco errori** finestra come avvisi o errori. Set di regole personalizzato può soddisfare esigenze per l'ambiente di sviluppo specifico. Quando si personalizza un set di regole, vengono fornite nella relativa pagina di ricerca e filtro gli strumenti per il processo.

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Fare pratica:** utilizzare set di strumenti di analisi codice per specificare una regola personalizzata per individuare e correggere i problemi in una semplice applicazione .NET Framework.|- [Procedura dettagliata: Configurazione e l'utilizzo di un Set di regole personalizzato](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Configurare l'analisi codice per un progetto:** scegliere una regole esistente impostato per un progetto, un sito Web o una soluzione.|- [Procedura: configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />- [Utilizzo di set di regole per specificare le regole di C++ per l'esecuzione](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />- [Procedura: configurare l'analisi codice per un'applicazione Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />- [Procedura: specificare set di regole per più progetti in una soluzione](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Personalizzare un set di regole:** specificare regole da applicare al progetto.|- [Creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Comprendere i set di regole predefinite:** consente di visualizzare le regole di analisi di codice che costituiscono il set di regole predefinite.|- [Riferimento del set di regole di analisi codice](../code-quality/code-analysis-rule-set-reference.md)|
|**Integrare l'analisi del codice con Team Foundation Server:** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] check-in criteri consentono ai team di sviluppo per assicurarsi che tutte le archiviazioni codice soddisfino un set comune di standard di analisi codice.|- [Procedura: sincronizzare i set di regole di progetto di codice con i criteri di controllo del progetto Team](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|