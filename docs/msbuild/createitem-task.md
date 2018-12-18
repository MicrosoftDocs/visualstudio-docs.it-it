---
title: "Attività CreateItem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 26f3851380e4cb7820a10b203a5e7a1b6c96287b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="createitem-task"></a>Attività CreateItem
Inserisce elementi di input nelle raccolte di elementi. Questo consente di copiare gli elementi da un elenco all'altro.  
  
> [!NOTE]
>  Si tratta di un'attività deprecata. A partire da .NET Framework 3.5, è possibile posizionare i gruppi di elementi all'interno di elementi [Target](../msbuild/target-element-msbuild.md). Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).  
  
## <a name="attributes"></a>Attributi  
 Nella tabella che segue vengono descritti i parametri dell'attività `CreateItem` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalMetadata`|Parametro di matrice `String` facoltativo.<br /><br /> Specifica metadati aggiuntivi da associare agli elementi di output.  Specificare il nome e il valore dei metadati dell'elemento usando la sintassi seguente:<br /><br /> *NomeMetadati* `=` *ValoreMetadati*<br /><br /> Le coppie nome/valore di metadati devono essere separate da un punto e virgola. Se il nome o il valore contiene un punto e virgola o qualsiasi altro carattere speciale, questo deve essere preceduto dal carattere di escape. Per altre informazioni, vedere [Procedura: Usare caratteri di escape speciali in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli elementi da escludere dalla raccolta di elementi di output. Questo parametro può contenere specifiche di caratteri jolly. Per altre informazioni, vedere [Elementi ](../msbuild/msbuild-items.md) e [Procedura: Escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica gli elementi da includere nella raccolta di elementi di output. Questo parametro può contenere specifiche di caratteri jolly.|  
|`PreserveExistingMetadata`|Parametro `Boolean` facoltativo.<br /><br /> Se `True`, i metadati aggiuntivi vengono applicati solo se non sono ancora presenti.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente mostra come creare una nuova raccolta di elementi denominata `MySourceItemsWithMetadata` a partire dalla raccolta di elementi `MySourceItems`. L'attività `CreateItem` popola la nuova raccolta con elementi dell'elemento `MySourceItems`. A ogni elemento della nuova raccolta viene poi aggiunto un altro metadato denominato `MyMetadata` di valore `Hello`.  
  
 Al termine dell'esecuzione dell'attività, la raccolta di elementi `MySourceItemsWithMetadata` contiene gli elementi `file1.resx` e `file2.resx`, entrambi con voci di metadati per `MyMetadata`. La raccolta di elementi `MySourceItems` rimane invariata.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 La tabella seguente descrive il valore dell'elemento di output dopo l'esecuzione dell'attività. I metadati degli elementi vengono visualizzati tra parentesi dopo l'elemento.  
  
|Raccolta di elementi|Sommario|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)