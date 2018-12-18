---
title: Attività XmlPoke | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05bef838c905b12ba76d22bec901ae4eb3382c5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="xmlpoke-task"></a>Attività XmlPoke
Imposta i valori come specificato da una query XPath in un file XML.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `XmlPoke` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Namespaces`|Parametro `String` facoltativo.<br /><br /> Specifica gli spazi dei nomi per i prefissi della query XPath.|  
|`Query`|Parametro `String` facoltativo.<br /><br /> Specifica la query XPath.|  
|`Value`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file di output.|  
|`XmlInputPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica l'input XML come percorso di file.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)