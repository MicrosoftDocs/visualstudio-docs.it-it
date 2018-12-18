---
title: "Attività GenerateTrustInfo | Microsoft Docs"
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 35b31cbf81f1f740ca66a05b05e384adbddf397b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
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