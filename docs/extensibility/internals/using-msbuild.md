---
title: Uso di MSBuild | Microsoft Docs
description: MSBuild fornisce un formato XML estendibile per la creazione di file di progetto che descrivono completamente gli elementi di progetto da compilare, le attività di compilazione e le configurazioni di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8891d9674a952f0272855c8b9203109ad2e22468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090694"
---
# <a name="using-msbuild"></a>Uso di MSBuild
MSBuild fornisce un formato XML estendibile e ben definito per la creazione di file di progetto che descrivono completamente gli elementi di progetto da compilare, le attività di compilazione e le configurazioni di compilazione.

## <a name="general-msbuild-considerations"></a>Considerazioni generali su MSBuild
 I file di progetto MSBuild, ad esempio [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i file con estensione csproj e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] VBPROJ, contengono dati usati in fase di compilazione, ma possono anche contenere dati usati in fase di progettazione. I dati in fase di compilazione vengono archiviati usando le primitive MSBuild, inclusi elemento [Item (MSBuild)](../../msbuild/item-element-msbuild.md) ed [elemento Property (MSBuild)](../../msbuild/property-element-msbuild.md). I dati della fase di progettazione, ovvero i dati specifici per il tipo di progetto e gli eventuali sottotipi di progetto correlati, vengono archiviati in un file XML in formato libero riservato.

 MSBuild non dispone del supporto nativo per gli oggetti di configurazione, ma fornisce attributi condizionali per la specifica di dati specifici della configurazione. Ad esempio:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Per altre informazioni sugli attributi condizionali, vedere [costrutti condizionali](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Estensione di MSBuild per il tipo di progetto
 Le interfacce e le API di MSBuild sono soggette a modifiche nelle versioni future di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Pertanto, è consigliabile utilizzare le classi del Framework di pacchetto gestito (MPF) perché forniscono la schermatura dalle modifiche.

 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. È possibile trovare il codice sorgente e le istruzioni di compilazione in [MPF for Projects-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Di seguito sono riportate le classi MPF specifiche del progetto:

|Classe|Implementazione|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` la classe è un wrapper per gli elementi MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generatori di file singoli e attività MSBuild
 I generatori di file singoli sono accessibili solo in fase di progettazione, ma le attività di MSBuild possono essere utilizzate in fase di progettazione e di compilazione. Per garantire la massima flessibilità, utilizzare le attività MSBuild per trasformare e generare codice. Per ulteriori informazioni, vedere [strumenti personalizzati](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Vedi anche
- [Riferimenti a MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Strumenti personalizzati](../../extensibility/internals/custom-tools.md)
