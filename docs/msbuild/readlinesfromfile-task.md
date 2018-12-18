---
title: Attività ReadLinesFromFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f05bb6e3f12dde2fbfd17120b9e2d646cb6e9f59
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="readlinesfromfile-task"></a>Attività ReadLinesFromFile
Legge un elenco di elementi da un file di testo.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `ReadLinesFromFile` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`File`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file da leggere. Il file deve contenere un elemento in ogni riga.|  
|`Lines`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene le righe lette dal file.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'attività `ReadLinesFromFile` per creare gli elementi da un elenco in un file di testo. Gli elementi letti dal file vengono archiviati nella raccolta di elementi `ItemsFromFile`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
    </ItemGroup>  
  
    <Target Name="ReadFromFile">  
        <ReadLinesFromFile  
            File="@(MyTextFile)" >  
            <Output  
                TaskParameter="Lines"  
                ItemName="ItemsFromFile"/>  
        </ReadLinesFromFile>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Attività](../msbuild/msbuild-tasks.md)