---
title: Tipi di file di soluzioni e di progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cc172d53e326d5bb20668f6919e887eca39f582
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="project-and-solution-file-types"></a>Tipi di file di soluzioni e di progetto

Visual Studio supporta molti tipi di file. In una installazione specifica, i componenti installati determinano i tipi di file supportati. Questo argomento descrive i tipi di file di soluzione e di progetto supportati in alcune installazioni tipiche.

## <a name="solution-files-sln-and-suo"></a>File di soluzione (.sln e .suo)

Visual Studio usa due tipi di file (.sln e .suo) per archiviare le impostazioni delle soluzioni. Questi file, noti collettivamente come file di soluzione, forniscono a Esplora soluzioni le informazioni necessarie per visualizzare un'interfaccia grafica per la gestione dei file.

|Estensione|nome|Descrizione|
|---------------|----------|-----------------|
|sln|Soluzione Visual Studio|Organizza progetti, elementi di progetto ed elementi della soluzione nella soluzione.|
|suo|Solution User Options|Tiene traccia delle personalizzazioni a livello dell'utente apportate in Visual Studio, ad esempio i punti di interruzione.|

## <a name="project-files"></a>File di progetto

I progetti possono contenere molti tipi di file diversi. Ad esempio, i file di codice C# hanno l'estensione **.cs** e i file di C++ hanno l'estensione **.cpp**. Le risorse vengono archiviate nei file **.resx** e XAML nei file **XAML**. I file [App.config](../../ide/managing-application-settings-dotnet.md) contengono informazioni sull'applicazione che non devono essere incluse nel codice dell'applicazione&mdash; ad esempio le stringhe di connessione.

Per altre informazioni sui tipi di file nei progetti C++, vedere [Tipi di file creati per i progetti di Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>Vedere anche

[Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)