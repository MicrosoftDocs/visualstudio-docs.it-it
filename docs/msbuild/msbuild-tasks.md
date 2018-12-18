---
title: "Attività di MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e1de29741f11413d8829902635c1284aa6e5bce6
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-tasks"></a>Attività MSBuild
Una piattaforma di compilazione deve poter eseguire un numero illimitato di azioni durante il processo di compilazione. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa le *attività* per eseguire queste azioni. Un'attività è un'unità di codice eseguibile usata da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per eseguire operazioni di compilazione atomiche.  
  
## <a name="task-logic"></a>Logica delle attività  
 Il formato del file di progetto XML di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non può eseguire del tutto autonomamente le operazioni di compilazione, quindi è necessario implementare una logica delle attività al di fuori del file di progetto.  
  
 La logica di esecuzione di un'attività viene implementata come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>, definita nello spazio dei nomi <xref:Microsoft.Build.Framework>.  
  
 La classe dell'attività definisce anche i parametri di input e di output disponibili per l'attività nel file di progetto. Tutte le proprietà pubbliche impostabili non statiche non astratte esposte dalla classe dell'attività sono accessibili nel file di progetto se si inserisce un attributo corrispondente con lo stesso nome nell'elemento [Task](../msbuild/task-element-msbuild.md).  
  
 Per scrivere un'attività personalizzata, è sufficiente creare una classe gestita che implementi l'interfaccia <xref:Microsoft.Build.Framework.ITask>. Per altre informazioni, vedere [Scrittura di attività](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Esecuzione di un'attività da un file di progetto  
 Prima di eseguire un'attività nel file di progetto, è necessario eseguire il mapping del tipo nell'assembly che implementa l'attività al nome dell'attività con l'elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). In questo modo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sa dove cercare la logica di esecuzione dell'attività quando la trova nel file di progetto.  
  
 Per eseguire un'attività in un file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], creare un elemento con il nome dell'attività come figlio di un elemento `Target`. Se un'attività accetta i parametri, questi vengono passati come attributi dell'elemento.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Le proprietà e gli elenchi di elementi possono essere usati come parametri. Il codice seguente, ad esempio, chiama l'attività `MakeDir` e imposta il valore della proprietà `Directories` dell'oggetto `MakeDir` sul valore della proprietà `BuildDir` dichiarata nell'esempio precedente.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Le attività possono anche restituire informazioni al file di progetto, che è possibile archiviare in elementi o proprietà per un uso futuro. Il codice seguente, ad esempio, chiama l'attività `Copy` e archivia le informazioni dalla proprietà di output `CopiedFiles` nell'elenco di elementi `SuccessfullyCopiedFiles`.  
  
```xml  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Attività incluse  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include diverse attività, ad esempio [Copy](../msbuild/copy-task.md) per eseguire la copia dei file, [MakeDir](../msbuild/makedir-task.md) per creare le directory e [Csc](../msbuild/csc-task.md) per compilare i file di codice sorgente di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Per un elenco completo delle attività disponibili e informazioni sull'uso, vedere [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Attività sottoposte a override  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] cerca le attività in più posizioni. La prima posizione sono i file con estensione OverrideTasks archiviati nelle directory di .NET Framework. Le attività in questi file eseguono l'override delle altre attività con gli stessi nomi, incluse le attività nel file di progetto. La seconda posizione sono i file con estensione Tasks archiviati nelle directory di .NET Framework. Se l'attività non è presente in nessuna di queste posizioni, viene usata l'attività nel file di progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Scrittura di attività](../msbuild/task-writing.md)   
 [Attività inline](../msbuild/msbuild-inline-tasks.md)