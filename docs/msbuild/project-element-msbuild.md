---
title: Elemento Project (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bf347f135368b2452170e7ebfa9c987ed19adf77
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="project-element-msbuild"></a>Elemento Project (MSBuild)
Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .  

## <a name="syntax"></a>Sintassi  

```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Sdk... />
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Descrizione|  
|---------------|-----------------|  
|`DefaultTargets`|Attributo facoltativo.<br /><br /> Destinazione o destinazioni predefinite che saranno il punto di ingresso della compilazione se non è stata specificata alcuna destinazione. Per specificare più destinazioni, usare il punto e virgola (;) come delimitatore.<br /><br /> Se non viene specificata alcuna destinazione predefinita nell'attributo `DefaultTargets` né nella riga di comando di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] il motore esegue la prima destinazione nel file di progetto dopo che gli elementi [Import](../msbuild/import-element-msbuild.md) sono stati valutati.|  
|`InitialTargets`|Attributo facoltativo.<br /><br /> Destinazione o destinazioni iniziali da eseguire prima delle destinazioni specificate nell'attributo `DefaultTargets` o nella riga di comando. Per specificare più destinazioni, usare il punto e virgola (;) come delimitatore.|  
|`Sdk`|Attributo facoltativo. <br /><br /> Nome e versione facoltativa dell'SDK da usare per creare istruzioni Import implicite che vengono aggiunte al file PROJ. Se non viene specificata alcuna versione, MSBuild tenterà di risolvere una versione predefinita.  Ad esempio, `<Project Sdk="Microsoft.NET.Sdk" />` o `<Project Sdk="My.Custom.Sdk/1.0.0" />`.|  
|`ToolsVersion`|Attributo facoltativo.<br /><br /> Versione del set di strumenti usato da MSBuild per determinare i valori per $(MSBuildBinPath) e $(MSBuildToolsPath).|  
|`TreatAsLocalProperty`|Attributo facoltativo.<br /><br /> Nomi di proprietà che non verranno considerati come globali. Questo attributo impedisce a proprietà della riga di comando specifiche di eseguire l'override dei valori delle proprietà impostati in un file di progetto o di destinazioni e di tutte le importazioni successive. Per specificare più proprietà, usare il punto e virgola (;) come delimitatore.<br /><br /> Le proprietà globali in genere eseguono l'override dei valori delle proprietà impostati nel file di progetto o di destinazioni. Se la proprietà è elencata nel valore `TreatAsLocalProperty`, il valore della proprietà globale non esegue l'override dei valori della proprietà impostati in tale file e delle importazioni successive. Per altre informazioni, vedere [Procedura: Compilare gli stessi file di origine con opzioni diverse](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Nota:** per impostare le proprietà globali al prompt dei comandi, si usa l'opzione **/property** (o **/p**). È anche possibile impostare o modificare le proprietà globali per i progetti figlio in una compilazione a più progetti usando l'attributo `Properties` dell'attività di MSBuild. Per altre informazioni, vedere [Attività di MSBuild](../msbuild/msbuild-task.md).|  
|`Xmlns`|Attributo facoltativo.<br /><br /> Se specificato, l'attributo `xmlns` deve avere il valore "http://schemas.microsoft.com/developer/msbuild/2003".|  

### <a name="child-elements"></a>Elementi figlio  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento facoltativo.<br /><br /> Valuta gli elementi figlio per selezionare un set di elementi `ItemGroup` e/o di elementi `PropertyGroup` da valutare.|  
|[Import](../msbuild/import-element-msbuild.md)|Elemento facoltativo.<br /><br /> Consente a un file di progetto importare un altro file di progetto. Possono esistere zero o più elementi `Import` in un progetto.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Elemento di raggruppamento per singoli elementi. Gli elementi vengono specificati usando l'elemento [Item](../msbuild/item-element-msbuild.md). Possono esistere zero o più elementi `ItemGroup` in un progetto.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Elemento facoltativo.<br /><br /> Consente di rendere permanente informazioni non di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] in un file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Possono esistere zero o un elemento `ProjectExtensions` in un progetto.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Elemento di raggruppamento per singole proprietà. Le proprietà vengono specificate usando l'elemento [Property](../msbuild/property-element-msbuild.md). Possono esistere zero o più elementi `PropertyGroup` in un progetto.|
|[Sdk](../msbuild/sdk-element-msbuild.md)|Elemento facoltativo.<br /><br /> Fa riferimento a un SDK di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Questo elemento può essere usato come alternativa all'attributo Sdk.|  
|[Destinazione](../msbuild/target-element-msbuild.md)|Elemento facoltativo.<br /><br /> Contiene un set di attività da eseguire in sequenza in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Le attività vengono specificate usando l'elemento [Task](../msbuild/task-element-msbuild.md). Possono esistere zero o più elementi `Target` in un progetto.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Elemento facoltativo.<br /><br /> Consente di registrare attività in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Possono esistere zero o più elementi `UsingTask` in un progetto.|  

### <a name="parent-elements"></a>Elementi padre  
 Nessuno.  

## <a name="see-also"></a>Vedere anche  
 [Procedura: Specificare quale destinazione compilare per prima](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
