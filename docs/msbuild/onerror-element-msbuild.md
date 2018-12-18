---
title: Elemento OnError (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 787d1dd1f7ae9b005d1d61c5c0fb09a81f6dc17d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="onerror-element-msbuild"></a>Elemento OnError (MSBuild)
Fa in modo che vengano eseguite una o più destinazioni se l'attributo `ContinueOnError` è `false` per un'attività non riuscita.  

 \<Project>  
 \<Target>  
 \<OnError>  

## <a name="syntax"></a>Sintassi  

```  
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
 Nessuno.  

### <a name="parent-elements"></a>Elementi padre  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Destinazione](../msbuild/target-element-msbuild.md)|Elemento contenitore per le attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="remarks"></a>Note  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] esegue l'elemento `OnError` se una delle attività dell'elemento `Target` ha esito negativo con l'attributo `ContinueOnError` impostato su `ErrorAndStop` (o `false`). Quando l'attività ha esito negativo, vengono eseguite le destinazioni specificate nell'attributo `ExecuteTargets`. Se la destinazione include più di un elemento `OnError`, gli elementi `OnError` vengono eseguiti in sequenza quando l'attività ha esito negativo.  

 Per altre informazioni sull'attributo `ContinueOnError`, vedere [Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md). Per informazioni sulle destinazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).  

## <a name="example"></a>Esempio  
 Il codice seguente esegue le attività `TaskOne` e `TaskTwo`. Se `TaskOne` ha esito negativo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] valuta l'elemento `OnError` ed esegue la destinazione `OtherTarget`.  

```xml  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  

## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Destinazioni](../msbuild/msbuild-targets.md)
