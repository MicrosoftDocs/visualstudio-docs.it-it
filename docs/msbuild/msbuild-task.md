---
title: Attività MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a58235b724f97e3934ab620677e530fbd9ba9726
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747358"
---
# <a name="msbuild-task"></a>MSBuild (attività)
Compila progetti di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] da un altro progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività `MSBuild` .

| Parametro | Description |
|-----------------------------------| - |
| `BuildInParallel` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i progetti specificati nel parametro `Projects` vengono compilati in parallelo, se possibile. Il valore predefinito è `false`. |
| `Projects` | Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di progetto da compilare. |
| `Properties` | Parametro `String` facoltativo.<br /><br /> Elenco delimitato da punti e virgola di coppie nome/valore delle proprietà da applicare come proprietà globali al progetto figlio. Dal punto di vista delle funzionalità, l'impostazione di questo parametro equivale a impostare proprietà dotate dell'opzione **-property** quando si esegue la compilazione con [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Ad esempio:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Quando si passano le proprietà al progetto tramite il parametro `Properties`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crea a una nuova istanza del progetto anche se il file di progetto è già stato caricato. Dopo che è stata creata una nuova istanza del progetto, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] la considera un progetto diverso che ha proprietà globali diverse e può essere compilato in parallelo con altre istanze del progetto. Una configurazione per la versione, ad esempio, può essere compilata contemporaneamente a una configurazione per il debug. |
| `RebaseOutputs` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i percorsi relativi degli elementi di output di destinazione dai progetti compilati vengono modificati in modo da essere percorsi relativi al progetto chiamante. Il valore predefinito è `false`. |
| `RemoveProperties` | Parametro `String` facoltativo.<br /><br /> Specifica il set di proprietà globali da rimuovere. |
| `RunEachTargetSeparately` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] richiama le destinazioni nell'elenco passato a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] una alla volta, invece che contemporaneamente. Impostare questo parametro su `true` garantisce che le destinazioni successive vengano richiamate anche se le destinazioni richiamate prima hanno avuto esito negativo. In caso contrario, un errore di compilazione arresterà la chiamata di tutte le destinazioni successive. Il valore predefinito è `false`. |
| `SkipNonexistentProjects` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i file di progetto che non esistono sul disco verranno ignorati. In caso contrario, tali progetti genereranno un errore. |
| `StopOnFirstFailure` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, quando la compilazione di uno dei progetti non riesce, non verranno compilati altri progetti. Questo parametro non è attualmente supportato con la compilazione in parallelo (con più processori). |
| `TargetAndPropertyListSeparators` | Parametro `String[]` facoltativo.<br /><br /> Specifica un elenco di destinazioni e proprietà come metadati dell'elemento `Project`. Il carattere di escape verrà rimosso dai separatori prima dell'elaborazione. Ad esempio, %3B (";" preceduto da un carattere di escape) verrà considerato come ";" non preceduto da un carattere di escape. |
| `TargetOutputs` | Parametro di output di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Restituisce gli output delle destinazioni compilate da tutti i file di progetto. Vengono restituiti solo gli output dalle destinazioni specificate, non tutti gli output esistenti nelle destinazioni da cui le destinazioni dipendono.<br /><br /> Il parametro `TargetOutputs` contiene anche i metadati seguenti:<br /><br /> -   `MSBuildSourceProjectFile`: il file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] contenente la destinazione che imposta gli output.<br />-   `MSBuildSourceTargetName`: destinazione che imposta gli output. **Nota:**  per identificare gli output da ogni file di progetto o destinazione separatamente, eseguire l'attività `MSBuild` separatamente per ogni file di progetto o destinazione. Se si esegue l'attività `MSBuild` solo una volta per compilare tutti i file di progetto, gli output di tutte le destinazioni vengono raccolte in una sola matrice. |
| `Targets` | Parametro `String` facoltativo.<br /><br /> Specifica la destinazione o le destinazioni da compilare nei file di progetto. Usare un punto e virgola per separare le voci di un elenco di nomi di destinazione. Se nessuna destinazione viene specificata nell'attività `MSBuild`, vengono compilate le destinazioni predefinite specificate nei file di progetto. **Nota:**  le destinazioni devono essere presenti in tutti i file di progetto. In caso contrario, si verifica un errore di compilazione. |
| `ToolsVersion` | Parametro `String` facoltativo.<br /><br /> Specifica la `ToolsVersion` da usare quando si compilano i progetti passati a questa attività.<br /><br /> Consente a un'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di compilare un progetto destinato a una versione di .NET Framework diversa da quella specificata nel progetto. I valori validi sono `2.0`, `3.0` e `3.5`. Il valore predefinito è `3.5`. |
| `UnloadProjectsOnCompletion` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il progetto verrà scaricato al termine dell'operazione. |
| `UseResultsCache` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il risultato memorizzato nella cache verrà restituito, se presente.<br /><br />  Se si esegue l'attività MSBuild, il risultato di questa viene memorizzato nella cache in un ambito <br /><br /> (ProjectFileName, GlobalProperties) [TargetNames]<br /><br /> come elenco di elementi di compilazione. |

## <a name="remarks"></a>Osservazioni
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

 Diversamente da quando si usa l'[attività Exec](../msbuild/exec-task.md) per avviare *MSBuild.exe*, questa attività usa lo stesso processo di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per compilare i progetti figlio. L'elenco di destinazioni già compilate che possono essere ignorate viene condiviso tra le compilazioni padre e figlio. Questa attività è anche più veloce perché non vengono creati nuovi processi di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

 Questa attività può elaborare non solo i file di progetto, ma anche i file di soluzione.

 Tutte le configurazioni richieste da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per consentire la compilazione simultanea dei progetti, anche se coinvolgono un'infrastruttura remota (ad esempio, porte, protocolli, timeout, tentativi e così via), devono essere rese configurabili usando un file di configurazione. Se possibile, gli elementi di configurazione devono essere specificati come parametri dell'attività nell'attività `MSBuild`.

 A partire da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, i progetti di soluzione espongono TargetOutputs da tutti i sottoprogetti compilati.

## <a name="pass-properties-to-projects"></a>Passare proprietà a progetti
 Nelle versioni di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] precedenti a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, passare set di Proprietà diversi a progetti diversi elencati nell'elemento [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è complicato. Se è stato usato l'attributo Properties dell'[attività MSBuild](../msbuild/msbuild-task.md), l'impostazione è stata applicata a tutti i progetti in corso di compilazione, a meno che l'[attività MSBuild](../msbuild/msbuild-task.md) non sia stata divisa in batch e non siano state fornite proprietà diverse in modo condizionale per ogni progetto nell'elenco di elementi.

 In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, tuttavia, sono disponibili due nuovi elementi di metadati riservati, Properties e AdditionalProperties, che consentono di passare in modo flessibile proprietà diverse a seconda del progetto da compilare tramite l'[attività MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Questi nuovi elementi di metadati sono applicabili solo agli elementi passati nell'attributo Projects dell'[attività MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Vantaggi della compilazione a più processori
 Uno dei vantaggi principali derivanti dall'uso di questi nuovi metadati consiste nel compilare i progetti in parallelo in un sistema a più processori. I metadati consentono di consolidare tutti i progetti in un'unica chiamata all'[attività MSBuild](../msbuild/msbuild-task.md) senza dover eseguire attività di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di divisione in batch o condizionali. E quando si chiama un'unica [attività MSBuild](../msbuild/msbuild-task.md), tutti i progetti elencati nell'attributo Projects vengono compilati in parallelo, ma solo se l'attributo `BuildInParallel=true` è presente nell'[attività MSBuild](../msbuild/msbuild-task.md). Per altre informazioni, vedere [Compilare più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadati Properties
 Uno scenario comune è quello in cui si compilano più file di soluzione tramite l'[attività MSBuild](../msbuild/msbuild-task.md), usando però configurazioni della build diverse. Potrebbe essere necessario compilare la soluzione a1 usando la configurazione per il debug e la soluzione a2 usando la configurazione per la versione. In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 questo file di progetto sarà come il seguente:

> [!NOTE]
> Nell'esempio seguente "…" rappresenta file di soluzione aggiuntivi.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Usando i metadati Properties, tuttavia, è possibile semplificare l'operazione e usare una sola [attività MSBuild](../msbuild/msbuild-task.md), come illustrato di seguito:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <Properties>Configuration=Debug</Properties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"/>
    </Target>
</Project>
```

 \- oppure -

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Debug"/>
    </Target>
</Project>
```

## <a name="additionalproperties-metadata"></a>Metadati AdditionalProperties
 Si consideri lo scenario seguente, in cui due file di soluzione vengono compilati tramite l'[attività MSBuild](../msbuild/msbuild-task.md). Entrambi usano la configurazione per il rilascio, ma uno usa l'architettura x86 e l'altro l'architettura ia64. In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 è necessario creare più istanze dell'[attività MSBuild](../msbuild/msbuild-task.md): una per compilare il progetto con la configurazione per il rilascio con l'architettura x86 e l'altro con la configurazione per il rilascio con l'architettura ia64. Il file di progetto sarà come il seguente:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 Usando i metadati AdditionalProperties è possibile semplificare l'operazione e usare una sola [attività MSBuild](../msbuild/msbuild-task.md), come illustrato di seguito:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <AdditionalProperties>Architecture=x86
              </AdditionalProperties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <AdditionalProperties>Architecture=ia64
              </AdditionalProperties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Release"/>
    </Target>
</Project>
```

## <a name="example"></a>Esempio
 L'esempio seguente usa l'attività `MSBuild` per compilare i progetti specificati dalla raccolta di elementi `ProjectReferences`. Gli output di destinazione risultanti vengono archiviati nella raccolta di elementi `AssembliesBuiltByChildProjects`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ProjectReferences Include="*.*proj" />
    </ItemGroup>

    <Target Name="BuildOtherProjects">
        <MSBuild
            Projects="@(ProjectReferences)"
            Targets="Build">
            <Output
                TaskParameter="TargetOutputs"
                ItemName="AssembliesBuiltByChildProjects" />
        </MSBuild>
    </Target>

</Project>
```

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)