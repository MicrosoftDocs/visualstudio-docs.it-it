---
title: "Attività GetReferenceAssemblyPaths | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6063ca7f69d5dd04c0675090eb6c6deb3075bdf5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="getreferenceassemblypaths-task"></a>Attività GetReferenceAssemblyPaths
Restituisce i percorsi degli assembly di riferimento dei vari framework.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `GetReferenceAssemblyPaths` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`, senza considerare la parte del profilo del moniker. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica il moniker del framework di destinazione associato ai percorsi degli assembly di riferimento.|  
|`RootPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso radice da usare per generare il percorso dell'assembly di riferimento.|  
|`BypassFrameworkInstallChecks`|Parametro <xref:System.Boolean> facoltativo.<br /><br /> Se `true`, consente di ignorare i controlli di base eseguiti da `GetReferenceAssemblyPaths` per impostazione predefinita per garantire che determinati framework di runtime vengano installati, a seconda del framework di destinazione.|  
|`TargetFrameworkMonikerDisplayName`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome visualizzato per il moniker del framework di destinazione.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)