---
title: Elemento ItemDefinitionGroup (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 534bad91ad4b909d798def84630cf54b64cd6ccf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306059"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Elemento ItemDefinitionGroup (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'elemento `ItemDefinitionGroup` consente di definire un set di definizioni di elementi, ovvero valori di metadati applicati a tutti gli elementi nel progetto per impostazione predefinita. ItemDefinitionGroup ovvia alla necessità di usare l'[attività CreateItem](../msbuild/createitem-task.md) e l'[attività CreateProperty](../msbuild/createproperty-task.md). Per altre informazioni, vedere [Definizioni degli elementi](../msbuild/item-definitions.md).  
  
 \<Project>  
 \<ItemDefinitionGroup>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo. Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione. Possono esistere zero o più elementi `Item` in un `ItemDefinitionGroup`.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente definisce due elementi di metadati, m e n, in un ItemDefinitionGroup. In questo esempio il metadato predefinito "m" viene applicato all'elemento "i" perché non è definito in modo esplicito dall'elemento "i". Al contrario, il metadato predefinito "n" non viene applicato all'elemento "i" perché è già definito dall'elemento "i".  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementi](../msbuild/msbuild-items.md)



