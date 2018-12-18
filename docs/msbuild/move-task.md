---
title: "Attività Move | Microsoft Docs"
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f4f0803767083a0a7302efe4c49c8524f4f2dd00
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="move-task"></a>Attività Move
Sposta i file in una nuova posizione.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Move`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`DestinationFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elenco di file in cui spostare i file di origine. Si presume che esista un mapping uno-a-uno tra questo elenco e quello specificato nel parametro `SourceFiles`. In altri termini, il primo file specificato in `SourceFiles` verrà spostato nel primo percorso specificato in `DestinationFiles` e così via.|  
|`DestinationFolder`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la directory in cui spostare i file.|  
|`MovedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi spostati correttamente.|  
|`OverwriteReadOnlyFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, sovrascrive i file anche se sono contrassegnati come di sola lettura.|  
|`SourceFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da spostare.|  
  
## <a name="remarks"></a>Note  
 È necessario specificare il parametro `DestinationFolder` o `DestinationFiles`, ma non entrambi. Se vengono specificati entrambi, l'attività avrà esito negativo e verrà registrato un errore.  

 L'attività `Move` crea le cartelle necessarie per i file di destinazione desiderati.

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
