---
title: "Attività RequiresFramework35SP1Assembly | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e95632e1b339e7b86253763fa65237165eb05618
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="requiresframework35sp1assembly-task"></a>Attività RequiresFramework35SP1Assembly
Determina se l'applicazione richiede .NET Framework 3.5 SP1.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `RequiresFramework35SP1Assembly` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Assemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly a cui si fa riferimento nell'applicazione.|  
|`CreateDesktopShortcut`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, crea un'icona di collegamento sul desktop durante l'installazione.|  
|`DeploymentManifestEntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file manifesto per l'applicazione.|  
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica l'assembly che deve essere eseguito quando viene eseguita l'applicazione.|  
|`ErrorReportUrl`|Parametro `String` facoltativo.<br /><br /> Specifica il sito Web visualizzato nelle finestre di dialogo che si aprono durante le installazioni ClickOnce.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elenco dei file che verranno distribuiti quando si pubblica l'applicazione.|  
|`ReferencedAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly a cui si fa riferimento nel progetto.|  
|`RequiresMinimumFramework35SP1`|Parametro di ouput facoltativo `Boolean`.<br /><br /> Se `true`, l'applicazione richiede .NET Framework 3.5 SP1.|  
|`SigningManifests`|Parametro di ouput facoltativo `Boolean`.<br /><br /> Se `true`, i manifesti ClickOnce sono firmati.|  
|`SuiteName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome della cartella del menu **Start** in cui verrà installata l'applicazione.|  
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione di .NET Framework a cui è destinata l'applicazione.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)