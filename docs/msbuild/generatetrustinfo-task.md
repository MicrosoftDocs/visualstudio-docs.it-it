---
title: Attività GenerateTrustInfo | Microsoft Docs
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b860caf26e15673044ede1a7790a1826c49b1fc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="generatetrustinfo-task"></a>Attività GenerateTrustInfo
Genera l'attendibilità dell'applicazione dal manifesto di base e dai parametri `TargetZone` e `ExcludedPermissions`.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `GenerateTrustInfo` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ApplicationDependencies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly dipendenti.|  
|`BaseManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il manifesto di base da cui generare l'attendibilità dell'applicazione.|  
|`ExcludedPermissions`|Parametro `String` facoltativo.<br /><br /> Specifica uno o più valori di identità di autorizzazione separati da un punto e virgola da escludere dal set di autorizzazioni predefinito per l'area.|  
|`TargetZone`|Parametro `String` facoltativo.<br /><br /> Specifica un set di autorizzazioni predefinito per l'area, ottenuto dai criteri del computer.|  
|`TrustInfoFile`|Parametro di ouput <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file che contiene le informazioni sull'attendibilità della sicurezza dell'applicazione.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)