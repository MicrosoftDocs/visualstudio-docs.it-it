---
title: Elemento OnError (MSBuild) | Microsoft Docs
description: Informazioni su come MSBuild utilizza l'elemento OnError per determinare l'esecuzione di una o più destinazioni, se l'attributo ContinueOnError è false per un'attività non riuscita.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 574f49b65f47b4a22240ca68b4d74c90ee580a15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905345"
---
# <a name="onerror-element-msbuild"></a>Elemento OnError (MSBuild)

Fa in modo che vengano eseguite una o più destinazioni se l'attributo `ContinueOnError` è `false` per un'attività non riuscita.

 \<Project> \<Target>
 \<OnError>

## <a name="syntax"></a>Sintassi

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Attributo obbligatorio.<br /><br /> Le destinazioni da eseguire se un'attività non riesce. Se si specificano più destinazioni, separarle con punto e virgola. Le destinazioni vengono eseguite nell'ordine specificato.|

### <a name="child-elements"></a>Elementi figlio

 Nessuna.

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Destinazione](../msbuild/target-element-msbuild.md) | Elemento contenitore per le attività di MSBuild. |

## <a name="remarks"></a>Commenti

 MSBuild esegue l' `OnError` elemento se una delle attività dell' `Target` elemento ha esito negativo con l' `ContinueOnError` attributo impostato su `ErrorAndStop` (o `false` ). Quando l'attività ha esito negativo, vengono eseguite le destinazioni specificate nell'attributo `ExecuteTargets`. Se la destinazione include più di un elemento `OnError`, gli elementi `OnError` vengono eseguiti in sequenza quando l'attività ha esito negativo.

 Per altre informazioni sull'attributo `ContinueOnError`, vedere [Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md). Per informazioni sulle destinazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).

## <a name="example"></a>Esempio

 Il codice seguente esegue le attività `TaskOne` e `TaskTwo`. Se ha `TaskOne` esito negativo, MSBuild valuta l' `OnError` elemento ed esegue la `OtherTarget` destinazione.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Vedi anche

- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
