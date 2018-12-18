---
title: Elemento PropertyGroup (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8df7de09fe90b0825d1b990b18b3a7d2309e4a08
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="propertygroup-element-msbuild"></a>Elemento PropertyGroup (MSBuild)
Contiene un set di elementi [Property](../msbuild/property-element-msbuild.md) definiti dall'utente. Ogni elemento `Property` usato in un progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve essere figlio di un elemento `PropertyGroup`.  

 \<Project>  
 \<PropertyGroup>  

## <a name="syntax"></a>Sintassi  

```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Descrizione|  
|---------------|-----------------|  
|Condizione|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementi figlio  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Property](../msbuild/property-element-msbuild.md)|Elemento facoltativo.<br /><br /> Nome proprietà definito dall'utente, che contiene il valore della proprietà. Possono esistere zero o più elementi *Property* in un elemento `PropertyGroup`.|  

### <a name="parent-elements"></a>Elementi padre  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come impostare le proprietà in base a una condizione. In questo esempio, se il valore della proprietà `CompileConfig` è `DEBUG`, vengono impostate le proprietà `Optimization`, `Obfuscate` e `OutputPath` nell'elemento `PropertyGroup`.  

```xml  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  

## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)  
 [Proprietà di MSBuild](../msbuild/msbuild-properties.md)
