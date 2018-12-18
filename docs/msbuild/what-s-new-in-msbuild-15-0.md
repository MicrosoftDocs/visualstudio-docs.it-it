---
title: Novità di MSBuild 15 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1757dc778c45d3b9c6afd7f289b6598728dc7687
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="whats-new-in-msbuild-15"></a>Novità di MSBuild 15
MSBuild è ora incluso in [.NET Core SDK](https://www.microsoft.com/net/download/core) e consente di compilare progetti .NET Core in Windows, macOS e Linux.  

## <a name="changed-path"></a>Percorso modificato
 MSBuild viene ora installato in una cartella in ogni versione di Visual Studio. Ad esempio `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`. Per individuare MSBuild, è anche possibile usare il modulo di PowerShell [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild non viene più installato nella Global Assembly Cache. Per fare riferimento a MSBuild a livello di codice, usare i pacchetti NuGet.

## <a name="changed-properties"></a>Proprietà modificate  
 In conseguenza del nuovo numero di versione le proprietà seguenti di MSBuild sono state modificate.  

-   Il valore di `MSBuildToolsVersion` per questa versione degli strumenti è 15.0. La versione dell'assembly è la 15.1.0.0.

-   Il percorso di `MSBuildToolsPath` non è più fisso. Per impostazione predefinita, si trova nella cartella MSBuild\15.0\Bin relativa al percorso di installazione di Visual Studio, ma è possibile che il percorso di installazione di Visual Studio venga modificato durante l'installazione.

-   I valori di `ToolsVersion` non vengono più impostato nel Registro di sistema.  

-   Le proprietà `SDK35ToolsPath` e `SDK40ToolsPath` puntano a .NET Framework SDK, incluso in un pacchetto con questa versione di Visual Studio, ad esempio 10.0A per gli strumenti 4.X.  

## <a name="updates"></a>Aggiornamenti
- Per l'[elemento Project](../msbuild/project-element-msbuild.md) è disponibile un nuovo attributo `SDK`. L'attributo `Xmlns` è ora facoltativo. Per altre informazioni, vedere [Pacchetti, metadati e framework](/dotnet/core/packages) e [Aggiunte al formato csproj per .NET Core](/dotnet/core/tools/csproj).
- Per l'[elemento Item](../msbuild/item-element-msbuild.md) esterno alle destinazioni è disponibile un nuovo attributo `Update`. È stata inoltre eliminata la restrizione relativa all'attributo `Remove`.
- `Directory.Build.props` è un file definito dall'utente che specifica le personalizzazioni dei progetti in una directory. Questo file viene importato automaticamente da Microsoft.Common.props, a meno che la proprietà `ImportDirectoryBuildTargets` non sia impostata su **false**. `Directory.Build.targets` viene importato da Microsoft.Common.targets.
- Eventuali metadati il cui nome non è in conflitto con l'elenco di attributi corrente possono essere espressi come un attributo. Per altre informazioni, vedere [Elemento Item](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nuove funzioni di proprietà

- `EnsureTrailingSlash` aggiunge una barra finale a un percorso se non ne esiste già una.
- `NormalizePath` combina gli elementi del percorso e assicura che la stringa di output includa i caratteri di separatore di directory corretti per il sistema operativo corrente.
- `NormalizeDirectory` combina gli elementi del percorso, aggiunge una barra finale e assicura che la stringa di output includa i caratteri di separatore di directory corretti per il sistema operativo corrente.
- `GetPathOfFileAbove` restituisce il percorso del file che precede quello corrente. Dal punto di vista funzionale equivale a una chiamata a `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`.

## <a name="see-also"></a>Vedere anche
[MSBuild](../msbuild/msbuild.md)
