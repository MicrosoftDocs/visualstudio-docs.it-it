---
title: Attività UpdateManifest | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0dd2ddfdbe784a45badfd0138b41b1f5dbff8ec7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641065"
---
# <a name="updatemanifest-task"></a>Attività UpdateManifest
Aggiorna le proprietà selezionate in un manifesto e ripete la firma.

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività `UpdateManifest` .

|Parametro|Description|
|---------------|-----------------|
|`ApplicationManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il manifesto dell'applicazione.|
|`ApplicationPath`|Parametro `String` obbligatorio.<br /><br /> Specifica il percorso del manifesto dell'applicazione.|
|`InputManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il manifesto da aggiornare.|
|`OutputManifest`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il manifesto che contiene le proprietà aggiornate.|

## <a name="remarks"></a>Osservazioni
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [Classe di base Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)