---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 963c53ed0cd1e74e3e641ac04012e5d0380980fe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)
Contiene un set di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente. Ogni elemento usato in un progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve essere specificato come figlio di un elemento `ItemGroup`.  
  
 \<Project>  
 \<ItemGroup>  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
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
|[Item](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione. Possono esistere zero o più elementi `Item` in un `ItemGroup`.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|[Destinazione](../msbuild/target-element-msbuild.md)|A partire da .NET Framework 3.5, l'elemento `ItemGroup` può essere visualizzato in un elemento `Target`. Per altre informazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).|  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra le raccolte di elementi definite dall'utente `Res` e `CodeFiles` in un elemento `ItemGroup`. Ogni elemento nella raccolta di elementi `Res` contiene un elemento [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) figlio definito dall'utente.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementi](../msbuild/msbuild-items.md)   
 [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)