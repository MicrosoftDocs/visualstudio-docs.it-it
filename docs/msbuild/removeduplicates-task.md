---
title: Attività RemoveDuplicates | Microsoft Docs
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d9e732d55858b713d73cbf1ba4f325f40560503
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987375"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates (attività)
Rimuove gli elementi duplicati dalla raccolta di elementi specificata.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `RemoveDuplicates` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`Filtered`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene una raccolta di elementi con tutti gli elementi duplicati rimossi. Viene rispettato l'ordine degli elementi di input, mantenendo la prima istanza di ogni elemento duplicato.|  
|`Inputs`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Raccolta di elementi da cui rimuovere gli elementi duplicati.|  
  
## <a name="remarks"></a>Note  
 In questa attività non viene fatta distinzione tra maiuscole e minuscole e non vengono confrontati i metadati quando si determinano i duplicati.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'attività `RemoveDuplicates` per rimuovere gli elementi duplicati dalla raccolta di elementi `MyItems`. Quando l'attività viene completata, la raccolta di elementi `FilteredItems` contiene un elemento.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

 L'esempio seguente dimostra che l'attività `RemoveDuplicates` mantiene il relativo ordine di input. Quando l'attività viene completata, la raccolta di elementi `FilteredItems` contiene gli elementi *MyFile2.cs*, *MyFile1.cs* e *MyFile3.cs* in questo ordine.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile2.cs"/>  
        <MyItems Include="MyFile1.cs" />  
        <MyItems Include="MyFile3.cs" />  
        <MyItems Include="myfile1.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

## <a name="see-also"></a>Vedere anche  
 [Attività MSBuild](../msbuild/msbuild-task-reference.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Attività](../msbuild/msbuild-tasks.md)
