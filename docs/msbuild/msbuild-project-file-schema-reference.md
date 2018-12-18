---
title: Informazioni di riferimento sullo schema del file di progetto di MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1911f7a6d5648c7940addf3301da2c818ad4f590
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-project-file-schema-reference"></a>Riferimenti dello schema del file di progetto MSBuild
Fornisce una tabella di tutti gli elementi di XML Schema di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] con gli attributi e gli elementi figlio disponibili.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa i file di progetto per indicare al motore di compilazione che cosa compilare e come compilarlo. I file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sono file XML che rispettano l'XML Schema di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Questa sezione documenta il file XSD (XML Schema Definition) per [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Elementi di XML Schema di MSBuild  
 La tabella seguente elenca tutti gli elementi di XML Schema di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] con gli elementi figlio e gli attributi.  
  
|Elemento|Elementi figlio|Attributi|  
|-------------|--------------------|----------------|  
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|  
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condizione<br /><br /> Progetto|  
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Import|Condizione|  
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condizione<br /><br /> Escludi<br /><br /> Includi<br /><br /> Rimuovi|  
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condizione|  
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condizione|  
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condizione|  
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condizione<br /><br /> ExecuteTargets|  
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Scegliere<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Elemento Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condizione<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Obbligatorio|  
|[ParameterGroup (elemento)](../msbuild/parametergroup-element.md)|*Parametro*|--|  
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Scegliere<br /><br /> Import<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> destinazione<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condizione|  
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Proprietà*|Condizione|  
|[Elemento Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|nome<br /><br /> Versione|  
|[Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Attività*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condizione<br /><br /> DependsOnTargets<br /><br /> Input<br /><br /> KeepDuplicateOutputs<br /><br /> nome<br /><br /> Output<br /><br /> Valore restituito|  
|[Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Condizione<br /><br /> ContinueOnError<br /><br /> *Parametro*|  
|[Elemento TaskBody (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dati*|Valutare|  
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condizione<br /><br /> TaskFactory<br /><br /> TaskName|  
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Scegliere<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condizione|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Condizioni](../msbuild/msbuild-conditions.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
