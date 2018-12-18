---
title: Utilizzare il Framework di pacchetto gestito per un tipo di progetto (c#) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112988f28728d40509a3af0360246a6bb4caef1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Utilizzando il Framework di pacchetto gestito per implementare un tipo di progetto (c#)
Il Framework di pacchetto gestito (MPF) fornisce le classi c# è possibile utilizzare o ereditare da per implementare i propri tipi di progetto. Il Framework MPF implementa molte delle interfacce di che Visual Studio prevede un tipo di progetto per fornire, permettendo a concentrarsi sull'implementazione delle indicazioni del tipo di progetto.  
  
## <a name="using-the-mpf-project-source-code"></a>Tramite il codice sorgente del progetto MPF  
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce le classi di supporto per la creazione e gestione di nuovo sistema di progetto. A differenza di altre classi di MPF, le classi del progetto non sono inclusi negli assembly forniti con Visual Studio. Al contrario, le classi del progetto vengono fornite come codice sorgente in [MPF per progetti 2013](http://mpfproj12.codeplex.com).  
  
 Per aggiungere questo progetto alla soluzione VSPackage, eseguire le operazioni seguenti:  
  
1.  Scaricare i file MPFProj *MPFProjectDir*.  
  
2.  Nel *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, modificare il blocco seguente:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Creare un progetto VSPackage.  
  
2.  Scaricare il progetto VSPackage.  
  
3.  Modificare il file con estensione csproj VSPackage aggiungendo il seguente blocco prima l'altro `<Import>` blocchi:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Salvare il progetto.  
  
2.  Chiudere e riaprire la soluzione di VSPackage.  
  
3.  Riaprire il progetto VSPackage. Verrà visualizzata una nuova directory denominata ProjectBase.  
  
4.  Aggiungere il seguente riferimento al progetto VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Compilare il progetto.  
  
## <a name="hierarchy-classes"></a>Gerarchia classi  
 Nella tabella seguente sono riepilogate le classi di MPFProj che supportano le gerarchie di progetto. Per ulteriori informazioni, vedere [gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nome di classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Classi di gestione di documenti  
 Nella tabella seguente sono elencate le classi MPF che supportano la gestione dei documenti. Per ulteriori informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nome di classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Configurazione e le classi di Output  
 Nella tabella seguente sono elencate le classi in MPF che consentono di tipi di progetto supporta più configurazioni, ad esempio il debug e rilascio e raccolte di output del progetto. Per ulteriori informazioni, vedere [la gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
|Nome di classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Classi di supporto di automazione  
 Nella tabella seguente sono elencate le classi MPF che supportano l'automazione in modo che gli utenti del tipo di progetto possono scrivere componenti aggiuntivi.  
  
|Nome di classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Classi di proprietà  
 La tabella seguente elenca le classi di MPF che tipi di progetto consente di aggiungono proprietà che gli utenti possono esplorare e modificare in un visualizzatore proprietà.  
  
|Nome di classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|