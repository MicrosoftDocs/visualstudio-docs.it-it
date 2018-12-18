---
title: Set di regole di analisi codice in Visual Studio
ms.date: 04/02/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a445aecdd5a9f02bca8d43e42646c991742a626
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Set di regole di utilizzo per raggruppare regole di analisi codice

Quando si configura l'analisi del codice in Visual Studio, è possibile scegliere da un elenco di incorporato *set di regole*. Un set di regole viene applicata a un progetto ed è un raggruppamento di codice le regole di analisi che identificano i problemi di destinazione e condizioni specifiche per il progetto. Ad esempio, è possibile applicare un set di regole che è progettato per l'analisi codice per le API disponibili pubblicamente, o solo le regole minime. È inoltre possibile applicare un set di regole che include tutte le regole.

È possibile personalizzare una set di regole mediante l'aggiunta o eliminazione di regole, o modificando i livelli di gravità regola vengono visualizzati come avvisi o errori nel **elenco errori**. Set di regole personalizzato può soddisfare esigenze per l'ambiente di sviluppo specifico. Quando si personalizza un set di regole, editor set di regole fornisce ricerca e strumenti per semplificare il processo di filtraggio.

## <a name="rule-set-format"></a>Formato del set di regole

Un set di regole viene specificato in formato XML in un *estensione ruleset* file. Regole, che sono costituiti da un ID e un *azione*, raggruppati per ID analizzatore e spazio dei nomi nel file.

Il contenuto XML di un *estensione ruleset* file avrà un aspetto simile al seguente:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> È più facile [modifica un set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md) nel grafico **Editor Set di regole** rispetto a mano.

La regola impostata per un progetto specificato per il `CodeAnalysisRuleSet` proprietà nel file di progetto Visual Studio. Ad esempio:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Vedere anche

- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)
