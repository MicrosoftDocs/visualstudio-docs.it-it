---
title: "Attività AssignProjectConfiguration | Microsoft Docs"
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
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7a4a803647afac9de77096e4a16d41987ff70c4f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="assignprojectconfiguration-task"></a>Attività AssignProjectConfiguration
Questa attività accetta stringhe di configurazione elenco e le assegna ai progetti specificati.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `AssignProjectConfiguration`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Parametro di ouput facoltativo `string`.<br /><br /> Include una stringa XML contenente una configurazione di progetto per ogni progetto. Le configurazioni vengono assegnate ai progetti con nome.|  
|`DefaultToVcxPlatformMapping`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene un elenco delimitato da punto e virgola dei mapping dai nomi di piattaforma usati<br /><br /> dalla maggior parte dei tipi a quelli usati da file con estensione vcxproj.<br /><br /> Ad esempio:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Facoltativo<br /><br /> Parametro di output `string`.<br /><br /> Contiene un elenco delimitato da punto e virgola dei mapping dai nomi di piattaforma con estensione vcxproj ai nomi di piattaforma usati dalla maggior parte dei tipi.<br /><br /> Ad esempio:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene la configurazione per il progetto corrente.|  
|`CurrentProjectPlatform`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene la piattaforma per il progetto corrente.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica che i riferimenti devono essere compilati anche se sono stati disabilitati nella configurazione del progetto.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica se la configurazione padre e la piattaforma devono essere annullate.|  
|`OutputType`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene il tipo di output per il progetto.|  
|`ResolveConfigurationPlatformUsingMappings`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica se la compilazione deve usare i mapping predefiniti per risolvere la configurazione e la piattaforma dei riferimenti del progetto passati.|  
|`AssignedProjects`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco dei percorsi dei riferimenti risolti.|  
|`UnassignedProjects`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco degli elementi di riferimento del progetto che non sono stati risolti usando l'elenco di output prerisolto.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)