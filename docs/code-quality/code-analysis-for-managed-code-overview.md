---
title: Analisi del codice per il codice gestito in Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 727a63d122871ff452365eea66e9a6e63a7c67b0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Panoramica di analisi del codice per il codice gestito

Visual Studio 2017 analizza il codice gestito in due modi: con legacy *FxCop* analisi statica di assembly gestiti e con .NET Compiler Platform *analizzatori*. Questo argomento vengono illustrate l'analisi statica del codice FxCop. Per ulteriori informazioni sull'analisi del codice usando gli analizzatori di .NET Compiler Platform, vedere [Panoramica di Roslyn analizzatori](../code-quality/roslyn-analyzers-overview.md).

L'analisi del codice gestito analizza gli assembly gestiti e fornisce informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework.

Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.

## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (integrated development environment)

È possibile eseguire l'analisi del codice del progetto manualmente o automaticamente.

Per eseguire l'analisi codice ogni volta che si compila un progetto, selezionare **Attiva analisi codice in fase di compilazione** nella pagina delle proprietà del progetto. Per ulteriori informazioni, vedere [procedura: abilitare e disabilitare analisi del codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Per eseguire manualmente l'analisi del codice in un progetto, dalla barra dei menu scegliere **Analizza** > **Esegui analisi del codice** > **Esegui analisi del codice su \<progetto >**.

## <a name="rule-sets"></a>Set di regole

Regole di analisi del codice per il codice gestito raggruppate in [set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). È possibile usare uno dei set di regole standard Microsoft oppure è possibile [creare un set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md) per soddisfare esigenze specifiche.

## <a name="suppress-warnings"></a>Esclusione di avvisi

È in genere utile indicare se un avviso non è applicabile. In questo modo lo sviluppatore e altri individui che potrebbero esaminare il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.

L'eliminazione nell'origine degli avvisi viene implementata attraverso attributi personalizzati. Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Per ulteriori informazioni, vedere [esclusione di avvisi](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Se si esegue la migrazione di un progetto di Visual Studio 2017, possono incontrare improvvisamente con un numero elevato di avvisi dell'analisi codice. Se non si è pronti per risolvere gli avvisi e si desidera aumentare la produttività sin da subito, puoi *linea di base* lo stato di analisi del progetto. Dal **Analizza** dal menu **Esegui analisi del codice ed Elimina problemi attivi**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Eseguire l'analisi del codice come parte dei criteri di archiviazione

Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri, tra cui, in particolare:

- Nel codice da archiviare non siano presenti errori di compilazione.

- Analisi del codice viene eseguito come parte della compilazione più recente.

A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione. Per ulteriori informazioni, vedere [miglioramento della qualità del codice con i criteri di archiviazione del progetto Team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integrazione di team build

È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione. Per ulteriori informazioni, vedere [di compilazione e versione (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Vedere anche

- [Panoramica di Roslyn analizzatori](../code-quality/roslyn-analyzers-overview.md)
- [Uso di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
