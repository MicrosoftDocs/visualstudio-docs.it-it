---
title: Compilazione di più progetti in parallelo con MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164767c628a6b48a3d9479fdd4f7918f12093ea7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>Compilazione di più progetti in parallelo con MSBuild
È possibile utilizzare MSBuild per compilare più progetti più velocemente eseguendoli in parallelo. Per eseguire compilazioni in parallelo, è possibile utilizzare le impostazioni seguenti in un computer multicore o con più processori:  
  
-   L'opzione `/maxcpucount` a un prompt dei comandi.  
  
-   Il parametro dell'attività <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> in un attività MSBuild.  
  
> [!NOTE]
>  L'opzione **/verbosity** (**/v**) in una riga di comando può incidere sulle prestazioni di compilazione, che possono diminuire se il livello di dettaglio delle informazioni del log di compilazione è impostato su dettagliato o diagnostico, utilizzati per la risoluzione dei problemi. Per altre informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md) e [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="maxcpucount-switch"></a>Opzione /maxcpucount  
 Se si utilizza l'opzione `/maxcpucount`, o l'abbreviazione `/m`, tramite MSBuild è possibile creare il numero specificato di processi di MSBuild.exe eseguibili in parallelo. Questi processi sono noti anche come "processi di lavoro". Ogni processo di lavoro usa un componente principale o un processore separato, se disponibile, per compilare progetti mentre altri processori eventualmente disponibili ne compilano altri. Ad esempio, se si imposta questa opzione su un valore pari a "4", in MSBuild verranno creati quattro processi di lavoro per compilare il progetto.  
  
 Se si include l'opzione `/maxcpucount` senza specificare un valore, in MSBuild verranno utilizzati fino al numero massimo di processori presenti nel computer.  
  
 Per altre informazioni su questa opzione, introdotta in MSBuild 3.5, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
 Nell'esempio seguente viene indicato a MSBuild di utilizzare tre processi di lavoro. Se si utilizza questa configurazione, tramite MSBuild sarà possibile compilare tre progetti contemporaneamente.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3   
```  
  
## <a name="buildinparallel-task-parameter"></a>Parametro dell'attività BuildInParallel  
 `BuildInParallel` è un parametro booleano facoltativo di un'attività di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Quando `BuildInParallel` è impostato su `true` (il valore predefinito è `false`), vengono generati più processi di lavoro per compilare contemporaneamente il maggior numero possibile di progetti. Affinché questo approccio funzioni, è necessario che l'opzione `/maxcpucount` sia impostata su un valore maggiore di 1 e che il sistema sia almeno di tipo dual-core o che disponga di due o più processori.  
  
 Di seguito è riportato un esempio, tratto da microsoft.common.targets, che descrive come impostare il parametro `BuildInParallel`.  
  
```  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di più processori per la compilazione di progetti](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Scrittura di logger compatibili con più processori](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Blog di ottimizzazione del parallelismo di compilazione di C++](http://go.microsoft.com/fwlink/?LinkId=251457)
