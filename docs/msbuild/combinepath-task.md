---
title: Attività CombinePath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b73ddd4715d3abd29f87d7ef38a269d821733ba
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610282"
---
# <a name="combinepath-task"></a>attività CombinePath
Combina i percorsi specificati in un singolo percorso.

## <a name="task-parameters"></a>Parametri dell'attività
 La tabella seguente descrive i parametri dell'[attività CombinePath](../msbuild/combinepath-task.md).

|Parametro|Description|
|---------------|-----------------|
|`BasePath`|Parametro `String` obbligatorio.<br /><br /> Percorso base da combinare con gli altri percorsi. Può essere un percorso relativo, assoluto o vuoto.|
|`Paths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Elenco di singoli percorsi da combinare con l'oggetto BasePath per formare il percorso combinato. I percorsi possono essere relativi o assoluti.|
|`CombinedPaths`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Percorso combinato creato da questa attività.|

## <a name="remarks"></a>Osservazioni
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)