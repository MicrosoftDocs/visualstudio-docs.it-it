---
title: Attività Touch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c6f96c09755d5bce3b7586c749286bdbde3891c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="touch-task"></a>Attività Touch
Imposta l'ora di accesso e di modifica dei file.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Touch` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AlwaysCreate`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, crea file non ancora esistenti.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica la raccolta di file di cui aggiornare il timestamp.|  
|`ForceTouch`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, forza l'aggiornamento del timestamp anche se i file sono di sola lettura.|  
|`Time`|Parametro `String` facoltativo.<br /><br /> Specifica un'ora diversa da quella corrente. Il formato deve essere accettabile per il metodo <xref:System.DateTime.Parse%2A>.|  
|`TouchedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene la raccolta di elementi di cui è stato eseguito l'aggiornamento del timestamp.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'attività `Touch` viene usata per modificare l'ora di accesso e di modifica dei file specificati nella raccolta di elementi `Files` e per inserire l'elenco dei file di cui è stato eseguito l'aggiornamento del timestamp nella raccolta di elementi `FilesTouched`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)