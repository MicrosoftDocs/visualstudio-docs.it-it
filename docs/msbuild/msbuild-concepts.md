---
title: Concetti relativi a MSBuild | Microsoft Docs
description: Informazioni su come specificare i componenti e i processi di compilazione usando proprietà, elementi, attività e destinazioni di MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f9b83c83f2826334b5f43d387a2d7c6941ba4d91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919179"
---
# <a name="msbuild-concepts"></a>Concetti relativi a MSBuild

MSBuild fornisce un XML Schema di base che è possibile utilizzare per controllare il modo in cui la piattaforma di compilazione compila il software. Per specificare i componenti nella compilazione e come devono essere compilati, usare queste quattro parti di MSBuild: proprietà, elementi, attività e destinazioni.

## <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [proprietà di MSBuild](../msbuild/msbuild-properties.md) | Introduce proprietà e raccolte di proprietà. Le proprietà sono coppie di chiave/valore che è possibile usare per configurare le compilazioni. |
| [Elementi MSBuild](../msbuild/msbuild-items.md) | Presenta gli elementi e le raccolte di elementi. Gli elementi sono input nel sistema di compilazione e, in genere, rappresentano i file. |
| [Destinazioni di MSBuild](../msbuild/msbuild-targets.md) | Spiega come raggruppare le attività in un dato ordine e consentire che determinate sezioni del processo di compilazione vengano richiamate dalla riga di comando. |
| [MSBuild (attività)](../msbuild/msbuild-tasks.md) | Viene illustrato come creare un'unità di codice eseguibile che può essere utilizzata da MSBuild per eseguire operazioni di compilazione atomiche. |
| [Confronto di proprietà ed elementi](../msbuild/comparing-properties-and-items.md) | Confronta le proprietà e gli elementi di MSBuild. Entrambi vengono usati per trasmettere informazioni ad attività, valutare condizioni e archiviare valori a cui poter fare riferimento nel file di progetto. |
| [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md) | Viene illustrato come eseguire l'escape di alcuni caratteri riserve da MSBuild per un uso speciale in contesti specifici. |
| [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Mostra come creare in modo incrementale un file di progetto di base usando soltanto un editor di testo. |
| [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md) | Introduce i blocchi predefiniti di MSBuild e mostra come scrivere, modificare ed eseguire il debug di progetti MSBuild senza chiudere l'ambiente di sviluppo integrato (IDE) di Visual Studio. |
| [Come vengono compilati i progetti in MSBuild](build-process-overview.md) | Descrive il processo di compilazione interno usato in MSBuild |
| [Riferimenti a MSBuild](../msbuild/msbuild-reference.md) | Collegamenti a documenti che contengono informazioni di riferimento. |
| [MSBuild](../msbuild/msbuild.md) | Presenta una panoramica di XML Schema per un file di progetto e illustra come controllare i processi che compilano il software. |
