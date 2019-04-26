---
title: File con estensione targets di MSBuild | Microsoft Docs
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04f85cf678052427ca5395c8b33c4786c2316de0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443627"
---
# <a name="msbuild-targets-files"></a>File con estensione targets di MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include più file con estensione *targets* che contengono elementi, proprietà, destinazioni e attività per scenari comuni. Questi file vengono automaticamente importati nella maggior parte dei file di progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per semplificare la manutenzione e la leggibilità.

 I progetti importano generalmente uno o più file con estensione *targets* per definire il processo di compilazione. Ad esempio, un progetto di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] creato da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importerà *Microsoft.CSharp.targets* che importa *Microsoft.Common.targets*. Il progetto stesso di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] definirà gli elementi e le proprietà specifici di tale progetto, ma le regole di compilazione standard per un progetto di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] vengono definite nei file con estensione *targets* importati.

 Il valore `$(MSBuildToolsPath)` specifica il percorso di questi file comuni con estensione *targets*. Se `ToolsVersion` è 4.0, i file si trovano nel percorso seguente: *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> Per informazioni su come creare destinazioni personalizzate, vedere [Destinazioni](../msbuild/msbuild-targets.md). Per informazioni su come usare l'elemento `Import` per inserire un file di progetto in un altro file di progetto, vedere [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) e [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>File comuni con estensione targets

| File con estensione *targets* | Description |
|---------------------------------| - |
| *Microsoft.Common.targets* | Definisce i passaggi nel processo di compilazione standard per i progetti di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importato dai file *Microsoft.CSharp.targets* e *Microsoft.VisualBasic.targets*, che includono l'istruzione seguente: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Definisce i passaggi nel processo di compilazione standard per i progetti di Visual C#.<br /><br /> Importato da file di progetto di Visual C# (con estensione *csproj*), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Definisce i passaggi nel processo di compilazione standard per i progetti di Visual Basic.<br /><br /> Importato da file di progetto di Visual Basic (con estensione *vbproj*), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets
*Directory.Build.targets* è un file definito dall'utente che specifica le personalizzazioni dei progetti in una directory. Questo file viene importato automaticamente da *Microsoft.Common.targets*, a meno che la proprietà **ImportDirectoryBuildTargets** sia impostata su **False**.

## <a name="see-also"></a>Vedere anche
- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
