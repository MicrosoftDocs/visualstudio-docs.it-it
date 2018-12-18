---
title: Elemento Parameter | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
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
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1ae8927c8a8f3a3fcd3f57075de281e3ee0679a1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="parameter-element"></a>Elemento Parameter
Contiene informazioni su un parametro specifico per un'attività generata da un oggetto `UsingTask``TaskFactory`.  Il nome dell'elemento è il nome del parametro.  Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  

## <a name="syntax"></a>Sintassi  

```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Descrizione|  
|---------------|-----------------|  
|`ParameterType`|Attributo facoltativo.<br /><br /> Il tipo .NET del parametro, ad esempio, "System.String".|  
|`Output`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro di output per l'attività. Per impostazione predefinita, il valore è `false`.|  
|`Required`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro obbligatorio per l'attività. Per impostazione predefinita, il valore è `false`.|  

### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  

### <a name="parent-elements"></a>Elementi padre  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene un elenco facoltativo di parametri che saranno presenti sull'attività generata da un oggetto `UsingTask``TaskFactory`.|  

## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'elemento `Parameter`.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
