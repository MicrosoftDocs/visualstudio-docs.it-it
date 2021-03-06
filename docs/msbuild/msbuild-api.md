---
title: API MSBuild | Microsoft Docs
description: Informazioni sulla superficie dell'API pubblica fornita da MSBuild, in modo che il programma possa eseguire compilazioni ed esaminare i progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b376f1cb1d6b473c0ea37bb33f6ae2b60789fa24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919301"
---
# <a name="use-the-msbuild-api"></a>Uso dell'API MSBuild

MSBuild fornisce una superficie dell'API pubblica per consentire al programma di eseguire le compilazioni e verificare i progetti. È possibile trovare le versioni recenti delle API di MSBuild nei pacchetti NuGet seguenti:

| Nome del pacchetto | Descrizione |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | Contiene l'assembly Microsoft. Build utilizzato per creare, modificare e valutare i progetti MSBuild.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Contiene l'assembly del Framework MSBuild comune usato da altri assembly MSBuild. |
| [Microsoft. Build. Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Recapita una copia eseguibile completa di MSBuild. Fare riferimento a questo pacchetto solo se l'applicazione deve caricare progetti o eseguire compilazioni in-process senza richiedere l'installazione di MSBuild. Per valutare correttamente i progetti che usano questo pacchetto, è necessario aggregare componenti aggiuntivi, ad esempio i compilatori, in una directory dell'applicazione. |
| [Microsoft. Build. Tasks. Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Contiene l'assembly Microsoft. Build. Tasks che implementa le attività di uso comune di MSBuild. |
| [Microsoft. Build. Utilities. Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Contiene l'assembly Microsoft. Build. Utilities utilizzato per implementare attività MSBuild personalizzate. |

Inoltre, NuGet ospita anche un assembly legacy, [Microsoft. Build. Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), che è deprecato.

Esistono diverse versioni dell'API MSBuild e per le versioni 15 e 16 sono presenti due forme distinte degli assembly nei pacchetti NuGet, una compilata con il .NET Framework e un'altra compilata con .NET Core, che è un subset della superficie dell'API .NET Framework.  La versione .NET Core di MSBuild viene usata quando si richiama il `dotnet` comando e quando si usa MSBuild nei sistemi Mac e Linux.

La documentazione per l'API MSBuild è disponibile tramite il [browser API .NET](/dotnet/api)oppure esplorando gli spazi dei nomi nell'elenco seguente.

::: moniker range="vs-2017"
| Spazio dei nomi | Si applica a | Descrizione |
|-----------| -----------| ----------- |
| [Microsoft. Build. costruzione](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Tutti |  Contiene i tipi utilizzati dal modello a oggetti MSBuild per costruire le radici del progetto con valori non valutati. Ogni radice di progetto corrisponde a un file di progetto o targets. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Tutti | Contiene la `ProjectOptions` classe che supporta la costruzione del progetto. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per valutare i progetti. Ogni progetto è associato a una o più radici di progetto. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Tutti | Contiene la `EvaluationContext` classe, utilizzata per archiviare lo stato di valutazione tra le chiamate. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi di eccezione che è possibile generare durante il processo di compilazione. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per compilare i progetti. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi che definiscono come avviene l'interazione di attività e logger con il motore MSBuild.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi che supportano la profilatura delle prestazioni. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | Solo .NET Framework | Contiene le classi utilizzate per rappresentare i tipi XAML analizzati da file, regole e altre origini. |
| [Microsoft. Build. Glob](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Tutti | Contiene classi che supportano l'elaborazione con caratteri jolly. |
| [Microsoft. Build. glob. Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi che supportano le estensioni per l'elaborazione con caratteri jolly. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi che supportano l' `-graph` opzione MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi utilizzati per la registrazione dello stato di avanzamento di una compilazione. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi che supportano la comunicazione remota in MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Tutti | Contiene l'implementazione di tutte le attività disponibili in MSBuild. |
| [Microsoft. Build. Tasks. Deployment. Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | Solo .NET Framework | Contiene classi usate internamente da MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | Solo .NET Framework | Contiene le classi usate da MSBuild.|
| [Microsoft. Build. Tasks. Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Tutti | Contiene classi usate internamente da MSBuild. |
| [Microsoft. Build. Tasks. XAML](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | Solo .NET Framework | Contiene le classi correlate alle attività di compilazione XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Tutti | Contiene le classi helper che è possibile usare per creare i logger e le attività di MSBuild.|
:::moniker-end
:::moniker range=">=vs-2019"
| Spazio dei nomi | Si applica a | Descrizione |
|-----------| -----------| ----------- |
| [Microsoft. Build. costruzione](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Tutti |  Contiene i tipi utilizzati dal modello a oggetti MSBuild per costruire le radici del progetto con valori non valutati. Ogni radice di progetto corrisponde a un file di progetto o targets. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Tutti | Contiene la `ProjectOptions` classe che supporta la costruzione del progetto. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per valutare i progetti. Ogni progetto è associato a una o più radici di progetto. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Tutti | Contiene la `EvaluationContext` classe, utilizzata per archiviare lo stato di valutazione tra le chiamate. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi di eccezione che è possibile generare durante il processo di compilazione. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per compilare i progetti. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi che definiscono come avviene l'interazione di attività e logger con il motore MSBuild.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi che supportano la profilatura delle prestazioni. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | Solo .NET Framework | Contiene le classi utilizzate per rappresentare i tipi XAML analizzati da file, regole e altre origini. |
| [Microsoft. Build. Glob](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Tutti | Contiene classi che supportano l'elaborazione con caratteri jolly. |
| [Microsoft. Build. glob. Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi che supportano le estensioni per l'elaborazione con caratteri jolly. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi che supportano l' `-graph` opzione MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi utilizzati per la registrazione dello stato di avanzamento di una compilazione. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi che supportano la comunicazione remota in MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Tutti | Contiene l'implementazione di tutte le attività disponibili in MSBuild. |
| [Microsoft. Build. Tasks. Deployment. Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | Solo .NET Framework | Contiene classi usate internamente da MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | Solo .NET Framework | Contiene le classi usate da MSBuild.|
| [Microsoft. Build. Tasks. Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Tutti | Contiene classi usate internamente da MSBuild. |
| [Microsoft. Build. Tasks. XAML](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | Solo .NET Framework | Contiene le classi correlate alle attività di compilazione XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Tutti | Contiene le classi helper che è possibile usare per creare i logger e le attività di MSBuild.|
:::moniker-end

Nella tabella precedente, all nella colonna si applica a significa che i tipi nello spazio dei nomi sono disponibili sia nella .NET Framework che nelle versioni di .NET Core dell'API MSBuild.
