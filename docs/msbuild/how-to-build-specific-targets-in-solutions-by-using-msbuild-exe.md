---
title: Usare MSBuild.exe per compilare destinazioni specifiche all'interno di soluzioni
description: Informazioni su come usare MSBuild.exe riga di comando per compilare destinazioni specifiche di progetti specifici nelle soluzioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ede73e06575a91cf9bdf8115942c27b1ce4e2841
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914463"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Procedura: Compilare destinazioni specifiche in soluzioni tramite MSBuild.exe

È possibile usare *MSBuild.exe* per compilare destinazioni specifiche di progetti specifici in una soluzione.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Per compilare una destinazione specifica di un progetto specifico in una soluzione

1. Nella riga di comando digitare `MSBuild.exe <SolutionName>.sln`, dove `<SolutionName>` corrisponde al nome file della soluzione che contiene la destinazione che si vuole eseguire.

2. Specificare la destinazione dopo l' `-target:` opzione nel formato \<ProjectName> : \<TargetName> . Se il nome del progetto contiene i caratteri `%`, `$`, `@`, `;`, `.`, `(`, `)` o `'`, sostituirli con `_` nel nome di destinazione specificato.

## <a name="example"></a>Esempio

 L'esempio seguente esegue la destinazione `Rebuild` del progetto `NotInSlnFolder` e quindi esegue la destinazione `Clean` del progetto `InSolutionFolder`, che si trova nella cartella della soluzione *NewFolder*.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si desidera esaminare le opzioni disponibili, è possibile usare un'opzione di debug fornita da MSBuild a questo scopo. Impostare la variabile di ambiente `MSBUILDEMITSOLUTION=1` e compilare la soluzione. Verrà generato un file MSBuild denominato *\<SolutionName> . sln. metaproj* che mostra la visualizzazione interna di MSBuild della soluzione in fase di compilazione. È possibile esaminare questa visualizzazione per determinare le destinazioni disponibili per la compilazione.

Non compilare con questa variabile di ambiente impostata a meno che non sia necessaria questa visualizzazione interna. Questa impostazione può causare problemi durante la compilazione dei progetti nella soluzione. In alternativa, cercare nel [log binario](obtaining-build-logs-with-msbuild.md#save-a-binary-log) .

## <a name="see-also"></a>Vedi anche

- [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
