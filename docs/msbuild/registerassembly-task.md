---
title: Attività RegisterAssembly | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e8c45e966c83549f2bb99a5ba8d6a2b7cd9d15f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="registerassembly-task"></a>Attività RegisterAssembly
Legge i metadati all'interno dell'assembly specificato e aggiunge le voci necessarie al Registro di sistema, consentendo ai client COM di creare classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in modo trasparente. Il comportamento di questa attività è simile, ma non identico, a quello di [Regasm.exe (strumento di registrazione dell'assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `RegisterAssembly` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Assemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica gli assembly da registrare con COM.|  
|`AssemblyListFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Contiene informazioni sullo stato tra l'attività `RegisterAssembly` e l'attività [UnregisterAssembly](../msbuild/unregisterassembly-task.md). Ciò impedisce all'attività `UnregisterAssembly` di tentare l'annullamento della registrazione di un assembly che non è riuscito a eseguire la registrazione nell'attività `RegisterAssembly`.|  
|`CreateCodeBase`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene creata una voce della codebase nel Registro di sistema, che specifica il percorso di un assembly non installato nella Global Assembly Cache. È consigliabile non specificare questa opzione se successivamente si intende installare nella Global Assembly Cache l'assembly che si sta registrando.|  
|`TypeLibFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica la libreria dei tipi da generare dall'assembly specificato. La libreria dei tipi generata contiene le definizioni dei tipi accessibili definiti all'interno dell'assembly. La libreria dei tipi viene generata solo se viene soddisfatta una delle condizioni seguenti:<br /><br /> -   Nel percorso specificato non è presente una libreria dei tipi con lo stesso nome.<br />-   La libreria dei tipi esistente è precedente all'assembly passato.<br /><br /> Se la libreria dei tipi è successiva all'assembly passato, non ne verrà creata una nuova ma l'assembly verrà comunque registrato.<br /><br /> Se questo parametro è specificato, è necessario che contenga lo stesso numero di elementi del parametro `Assemblies`. In caso contrario, l'attività avrà esito negativo. Se non è specificato alcun valore, il nome dell'assembly verrà usato per impostazione predefinita e l'estensione dell'elemento verrà modificata in tlb.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'attività `RegisterAssembly` viene usata per registrare l'assembly specificato dalla raccolta di elementi `MyAssemblies`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)