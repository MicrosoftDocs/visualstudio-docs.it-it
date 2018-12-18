---
title: Attività MakeDir | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44a87542e6bc2f28be841020b588c2d6ab3be683
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="makedir-task"></a>Attività MakeDir
Crea directory e, se necessario, eventuali directory padre.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `MakeDir` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Directories`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Set di directory da creare.|  
|`DirectoriesCreated`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Le directory create dall'attività. Se non è stato possibile creare alcune directory, può non contenere tutti gli elementi passati al parametro `Directories`.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene usata l'attività `MakeDir` per creare la directory specificata dalla proprietà `OutputDirectory`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)