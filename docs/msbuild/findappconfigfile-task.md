---
title: Attività FindAppConfigFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf30e53f8d62f98b5e18b4e9a64e43d32aa498b0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="findappconfigfile-task"></a>Attività FindAppConfigFile
Trova il file app.config, se presente, negli elenchi forniti.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `FindAppConfigFile` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AppConfigFile`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il primo elemento corrispondente trovato nell'elenco, se presente.|  
|`PrimaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco principale in cui eseguire la ricerca.|  
|`SecondaryList`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco secondario in cui eseguire la ricerca.|  
|`TargetPath`|Parametro `String` obbligatorio.<br /><br /> Specifica il valore da aggiungere come metadati.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)