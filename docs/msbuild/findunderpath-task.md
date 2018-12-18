---
title: Attività FindUnderPath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84054917a47fc4d56c107965feebbc353e6de76f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="findunderpath-task"></a>Attività FindUnderPath
Determina gli elementi di una raccolta specificata i cui percorsi sono presenti nella cartella indicata e nelle relative sottocartelle.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `FindUnderPath` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file i cui percorsi devono essere confrontati con il percorso specificato dal parametro `Path`.|  
|`InPath`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi che sono stati trovati nel percorso specificato.|  
|`OutOfPath`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi che non sono stati trovati nel percorso specificato.|  
|`Path`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il percorso della cartella da usare come riferimento.|  
|`UpdateToAbsolutePaths`|Parametro `Boolean` facoltativo.<br /><br /> Se true, i percorsi degli elementi di output vengono aggiornati in modo da essere percorsi assoluti.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'attività `FindUnderPath` per determinare se i file contenuti nell'elemento `MyFiles` hanno percorsi esistenti nel percorso specificato dalla proprietà `SearchPath`. Al termine dell'attività, l'elemento `FilesNotFoundInPath` contiene il file `File1.txt` e l'elemento `FilesFoundInPath` contiene il file `File2.txt`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)