---
title: Attività Unzip | Microsoft Docs
description: Informazioni sui parametri e sull'utilizzo dell'attività decomprimere MSBuild, che consente di decomprimere un archivio zip in un percorso specificato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 213d37108e37b9002b2241e6c0806d6d7db7caf6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902493"
---
# <a name="unzip-task"></a>Attività Unzip

Decomprime un archivio con estensione *zip* nella posizione specificata.

>[!NOTE]
>L'attività `Unzip` è disponibile solo in MSBuild 15.8 e versioni successive.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `Unzip` .

|Parametro|Descrizione|
|---------------|-----------------|
|`DestinationFolder`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio<br /><br /> Specifica la cartella di destinazione in cui decomprimere il file.|
|`OverwriteReadOnlyFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, sovrascrive i file di sola lettura. Il valore predefinito è `false`.|
|`SkipUnchangedFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, ignora i file decompressi che non hanno subito modifiche. Il valore predefinito è `true`. L'attività `Unzip` considera invariati i file con le stesse dimensioni e la stessa ora dell'ultima modifica.|
|`SourceFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica uno o più file da decomprimere. Quando si specificano più file, i file vengono decompressi nell'ordine nella stessa cartella.|

## <a name="remarks"></a>Commenti

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 L'esempio seguente decomprime un archivio e sovrascrive eventuali file di sola lettura.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
