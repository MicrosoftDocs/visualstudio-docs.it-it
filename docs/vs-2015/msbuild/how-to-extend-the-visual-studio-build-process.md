---
title: 'Procedura: Estendere il processo di compilazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 789c60da5be841721ab3a999120e2fe560ffd588
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156606"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Procedura: estendere il processo di compilazione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il processo di compilazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è definito da una serie di file di [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con estensione targets che vengono importati nel file di progetto. Uno di questi file importati, Microsoft.Common.targets, può essere esteso per consentire l'esecuzione di attività personalizzate in diversi punti del processo di compilazione. Questo argomento illustra due metodi che è possibile usare per estendere il processo di compilazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- Override di specifiche destinazioni predefinite in Microsoft.Common.targets.

- Override delle proprietà "DependsOn" definite in Microsoft.Common.targets.

## <a name="overriding-predefined-targets"></a>Override di destinazioni predefinite
 Il file Microsoft.Common.targets contiene un insieme di destinazioni predefinite vuote che vengono chiamate prima e dopo alcune delle destinazioni più importanti nel processo di compilazione. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], ad esempio, chiama la destinazione `BeforeBuild` prima della destinazione `CoreBuild` principale e la destinazione `AfterBuild` dopo la destinazione `CoreBuild`. Per impostazione predefinita, le destinazioni vuote in Microsoft.Common.targets non eseguono alcuna operazione, ma è possibile eseguire l'override del comportamento predefinito specificando le destinazioni desiderate in un file di progetto che importa Microsoft.Common.targets. In questo modo sarà possibile usare le attività di [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] per avere un controllo maggiore sul processo di compilazione.

#### <a name="to-override-a-predefined-target"></a>Per eseguire l'override di una destinazione predefinita

1. In Microsoft.Common.targets identificare una destinazione predefinita di cui si vuole eseguire l'override. Nella tabella seguente è riportato l'elenco completo delle destinazioni di cui è possibile eseguire l'override in totale sicurezza.

2. Definire le destinazioni alla fine del file di progetto, immediatamente prima del tag `</Project>`. Ad esempio:

   ```
   <Project>
       ...
       <Target Name="BeforeBuild">
           <!-- Insert tasks to run before build here -->
       </Target>
       <Target Name="AfterBuild">
           <!-- Insert tasks to run after build here -->
       </Target>
   </Project>
   ```

3. Compilare il file di progetto.

   Nella tabella seguente sono indicate tutte le destinazioni in Microsoft.Common.targets di cui è possibile eseguire l'override in totale sicurezza.

|Target Name|DESCRIZIONE|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la compilazione principale. La maggior parte delle personalizzazioni avviene in una di queste due destinazioni.|
|`BeforeBuild`, `AfterBuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo qualsiasi altra attività nella compilazione. **Nota:** le destinazioni `BeforeBuild` e `AfterBuild` sono già definite nei commenti alla fine della maggior parte dei file di progetto. Questo agevola l'aggiunta di eventi di pre-compilazione e post-compilazione al file di progetto.|
|`BeforeRebuild`, `AfterRebuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la ricompilazione. L'ordine di esecuzione delle destinazioni in Microsoft.Common.targets è: `BeforeRebuild`, `Clean`, `Build` e quindi `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pulitura.|
|`BeforePublish`, `AfterPublish`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pubblicazione.|
|`BeforeResolveReference`, `AfterResolveReferences`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la risoluzione dei riferimenti all'assembly.|
|`BeforeResGen`, `AfterResGen`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la generazione delle risorse.|

## <a name="overriding-dependson-properties"></a>Override delle proprietà "DependsOn"
 L'override delle destinazioni predefinite costituisce uno dei modi più semplici per estendere il processo di compilazione. Tuttavia, poiché [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] valuta la definizione delle destinazioni in modo sequenziale, non è possibile evitare che un altro progetto in cui viene importato il progetto in questione esegua l'override delle destinazioni di cui è già stato eseguito l'override. Di conseguenza, ad esempio, l'ultima destinazione `AfterBuild` definita nel file di progetto, al termine dell'importazione di tutti gli altri progetti, sarà quella usata durante la compilazione.

 Per evitare override indesiderati di destinazioni, è possibile eseguire l'override delle proprietà "DependsOn" usate negli attributi `DependsOnTargets` del file Microsoft.Common.targets. Nella destinazione `Build`, ad esempio, il valore dell'attributo `DependsOnTargets` è `"$(BuildDependsOn)"`. Tenere presente quanto segue:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Questa parte di codice XML indica che la destinazione `Build` può essere eseguita solo dopo l'esecuzione di tutte le destinazioni specificate nella proprietà `BuildDependsOn`. La proprietà `BuildDependsOn` è definita come segue:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 È possibile eseguire l'override di questo valore di proprietà dichiarando un'altra proprietà denominata `BuildDependsOn` alla fine del file di progetto. L'inclusione della proprietà `BuildDependsOn` precedente nella nuova proprietà consente di aggiungere nuove destinazioni all'inizio e alla fine dell'elenco di destinazioni. Ad esempio:

```
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

 I progetti che importano i file di progetto possono eseguire l'override di queste proprietà senza sovrascrivere le personalizzazioni effettuate in precedenza.

#### <a name="to-override-a-dependson-property"></a>Per eseguire l'override di una proprietà "DependsOn"

1. In Microsoft.Common.targets identificare una proprietà "DependsOn" predefinita di cui si vuole eseguire l'override. Nella tabella che segue è riportato un elenco delle proprietà "DependsOn" comunemente sottoposte a override.

2. Definire un'altra istanza della proprietà o delle proprietà alla fine del file di progetto. Nella nuova proprietà includere la proprietà originale, ad esempio `$(BuildDependsOn)`.

3. Definire le destinazioni personalizzate prima o dopo la definizione della proprietà.

4. Compilare il file di progetto.

### <a name="commonly-overridden-dependson-properties"></a>Proprietà "DependsOn" comunemente sottoposte a override

|Nome proprietà|DESCRIZIONE|
|-------------------|-----------------|
|`BuildDependsOn`|Proprietà di cui eseguire l'override se si vuole inserire destinazioni personalizzate prima o dopo l'intero processo di compilazione.|
|`CleanDependsOn`|Proprietà di cui eseguire l'override se si vuole pulire l'output del processo di compilazione personalizzato.|
|`CompileDependsOn`|Proprietà di cui eseguire l'override se si vuole inserire processi personalizzati prima o dopo la fase di compilazione.|

## <a name="see-also"></a>Vedere anche
 [Integrazione di Visual Studio](../msbuild/visual-studio-integration-msbuild.md) [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md) [File con estensione targets](../msbuild/msbuild-dot-targets-files.md)
