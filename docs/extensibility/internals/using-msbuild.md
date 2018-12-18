---
title: Utilizzo di MSBuild | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4115d6f1b368734631acf3ee4395d71dbe418c07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-msbuild"></a>Utilizzo di MSBuild
MSBuild fornisce un formato XML ben definito ed estendibile per la creazione di file di progetto che la descrizione completa degli elementi di progetto per essere compilato, attività di compilazione e configurazioni di compilazione.  
  
## <a name="general-msbuild-considerations"></a>Considerazioni generali MSBuild  
 File di progetto MSBuild, ad esempio, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] con estensione csproj e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] vsproj, contengono dati che viene utilizzati in fase di compilazione, ma possono contenere anche dati che viene utilizzati in fase di progettazione. Dati della fase di compilazione vengono archiviati utilizzando le primitive di MSBuild, tra cui [elemento Item (MSBuild)](../../msbuild/item-element-msbuild.md) e [elemento Property (MSBuild)](../../msbuild/property-element-msbuild.md). In fase di progettazione dati, vale a dire dati specifici per il tipo di progetto e degli eventuali sottotipi di progetto correlate, verrà archiviate in formato libero XML riservato.  
  
 MSBuild non dispone del supporto nativo per gli oggetti di configurazione, ma fornire attributi condizionali per specificare i dati specifici della configurazione. Ad esempio:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Per ulteriori informazioni sugli attributi condizionali, vedere [costruisce condizionale](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Estensione di MSBuild per il tipo di progetto  
 Interfacce di MSBuild e API sono soggetti a modifiche nelle versioni future di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pertanto, è consigliabile utilizzare le classi di pacchetto gestito (MPF) framework in quanto forniscono schermatura dalle modifiche.  
  
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce le classi di supporto per la creazione e gestione di nuovo sistema di progetto. È possibile trovare l'origine istruzioni di compilazione e codice in [MPF per i progetti di Visual Studio 2013 -](http://mpfproj12.codeplex.com/).  
  
 Come indicato di seguito sono riportate le classi MPF specifici del progetto:  
  
|Classe|Implementazione|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` classe è un wrapper per gli elementi di MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Visual Studio di generatori di File singolo. Attività MSBuild  
 Singolo file i generatori sono accessibili in fase di progettazione solo, ma le attività MSBuild possono essere utilizzate in fase di progettazione e in fase di compilazione. Per la massima flessibilità, pertanto, utilizzare le attività MSBuild per trasformare e generare il codice. Per ulteriori informazioni, vedere [strumenti personalizzati](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [Strumenti personalizzati](../../extensibility/internals/custom-tools.md)