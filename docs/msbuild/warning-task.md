---
title: Attività Warning | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività di avviso per registrare un avviso durante una compilazione in base a un'istruzione condizionale valutata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f31ad26b6efffa540ecae6a61f0f7ff12115cef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933804"
---
# <a name="warning-task"></a>attività Warning

Registra un avviso durante una compilazione in base a un'istruzione condizionale valutata.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `Warning` .

| Parametro | Descrizione |
|---------------| - |
| `Code` | Parametro `String` facoltativo.<br /><br /> Il codice di avviso da associare all'avviso. |
| `File` | Parametro `String` facoltativo.<br /><br /> Specifica il file pertinente, se presente. Se non viene indicato alcun file, verrà usato il file contenente l'attività Warning. |
| `HelpKeyword` | Parametro `String` facoltativo.<br /><br /> Parola chiave della Guida da associare all'avviso. |
| `Text` | Parametro `String` facoltativo.<br /><br /> Testo di avviso che viene registrato da MSBuild se il `Condition` parametro restituisce `true` . |

## <a name="remarks"></a>Commenti

 L' `Warning` attività consente ai progetti MSBuild di verificare la presenza di una proprietà o una configurazione richiesta prima di procedere con l'istruzione di compilazione successiva.

 Se il parametro `Condition` dell'attività `Warning` restituisce `true`, verrà registrato il valore del parametro `Text` e l'esecuzione della compilazione continua. Se non esiste un parametro `Condition`, viene registrato il testo dell'avviso. Per altre informazioni sulla registrazione, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 Nell'esempio di codice seguente viene verificata la presenza di proprietà impostate nella riga di comando. Se non sono presenti proprietà impostate, il progetto genera un evento di avviso e registra il valore del parametro `Text` dell'attività `Warning`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
