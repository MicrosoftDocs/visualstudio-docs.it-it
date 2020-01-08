---
title: Concetti relativi a MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aed8c97702989bdbdfd0f09c3cf99391c12fe9bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589279"
---
# <a name="msbuild-concepts"></a>Concetti relativi a MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce un XML Schema di base che è possibile usare per controllare come la piattaforma di compilazione compila il software. Per specificare i componenti nella compilazione e come devono essere compilati, usare queste quattro parti di MSBuild: proprietà, elementi, attività e destinazioni.

## <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [Proprietà di MSBuild](../msbuild/msbuild-properties.md) | Introduce proprietà e raccolte di proprietà. Le proprietà sono coppie di chiave/valore che è possibile usare per configurare le compilazioni. |
| [Elementi MSBuild](../msbuild/msbuild-items.md) | Presenta gli elementi e le raccolte di elementi. Gli elementi sono input nel sistema di compilazione e, in genere, rappresentano i file. |
| [Destinazioni di MSBuild](../msbuild/msbuild-targets.md) | Spiega come raggruppare le attività in un dato ordine e consentire che determinate sezioni del processo di compilazione vengano richiamate dalla riga di comando. |
| [Attività MSBuild](../msbuild/msbuild-tasks.md) | Mostra come creare un'unità di codice eseguibile che [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può usare per eseguire operazioni di compilazione atomiche. |
| [Confronto di proprietà ed elementi](../msbuild/comparing-properties-and-items.md) | Confronta le proprietà e gli elementi di MSBuild. Entrambi vengono usati per trasmettere informazioni ad attività, valutare condizioni e archiviare valori a cui poter fare riferimento nel file di progetto. |
| [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md) | Illustra come usare caratteri di escape per alcuni caratteri che in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sono riservati a contesti specifici. |
| [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Mostra come creare in modo incrementale un file di progetto di base usando soltanto un editor di testo. |
| [Procedura dettagliata: uso di MSBuild](../msbuild/walkthrough-using-msbuild.md) | Introduce i blocchi predefiniti di MSBuild e mostra come scrivere, modificare ed eseguire il debug di progetti MSBuild senza chiudere l'ambiente di sviluppo integrato (IDE) di Visual Studio. |
| [Riferimenti a MSBuild](../msbuild/msbuild-reference.md) | Collegamenti a documenti che contengono informazioni di riferimento. |
| [MSBuild](../msbuild/msbuild.md) | Presenta una panoramica di XML Schema per un file di progetto e illustra come controllare i processi che compilano il software. |
