---
title: Elemento TaskBody (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45b255f782390cfc478ac2f7bce58170e4e2b268
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631848"
---
# <a name="taskbody-element-msbuild"></a>Elemento TaskBody (MSBuild)

Contiene i dati passati a un `UsingTask` `TaskFactory`. Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<TaskBody>

## <a name="syntax"></a>Sintassi

```xml
<TaskBody Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Evaluate`|Attributo booleano facoltativo.<br /><br /> Se `true`, MSBuild valuta tutti gli elementi interni ed espande gli elementi e le proprietà prima di passare le informazioni a `TaskFactory` quando viene creata un'istanza dell'attività.|

### <a name="child-elements"></a>Elemento figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Data|Il testo compreso tra i tag `TaskBody` viene inviato testualmente a `TaskFactory`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fornisce un modo per registrare le attività in MSBuild. Possono esistere zero o più elementi `UsingTask` in un progetto. |

## <a name="example"></a>Esempio

 L'esempio seguente illustra come usare l'elemento `TaskBody` con un attributo `Evaluate`.

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

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
