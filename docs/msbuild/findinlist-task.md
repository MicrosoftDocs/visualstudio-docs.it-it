---
title: "Attività FindInList | Microsoft Docs"
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ccf4f6b8f07da67af061c101f7f7b6500de48f73
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="findinlist-task"></a>Attività FindInList
Trova in un elenco specificato un elemento con un itemspec corrispondente.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività [FindInList](../msbuild/findinlist-task.md).  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`CaseSensitive`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, la ricerca fa distinzione tra maiuscole e minuscole, in caso contrario non la fa. Il valore predefinito è `true`.|  
|`FindLastMatch`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, restituisce l'ultima corrispondenza, in caso contrario restituisce la prima corrispondenza. Il valore predefinito è `false`.|  
|`ItemFound`|Parametro di output di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Il primo elemento corrispondente trovato nell'elenco, se presente.|  
|`ItemSpecToFind`|Parametro `String` obbligatorio.<br /><br /> L'argomento itemspec da cercare.|  
|`List`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> L'elenco in cui eseguire la ricerca dell'argomento itemspec.|  
|`MatchFileNameOnly`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene confrontata solo la parte del nome file dell'itemspec, in caso contrario l'intero itemspec. Il valore predefinito è `true`.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)