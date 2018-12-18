---
title: Costrutti condizionali di MSBuild | Microsoft Docs
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
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f018ec733248f6663e2cf2292599df9d2afdc81c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-conditional-constructs"></a>Costrutti condizionali di MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] offre un meccanismo per l'elaborazione di tipo o/o con gli elementi [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) e [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## <a name="using-the-choose-element"></a>Uso dell'elemento Choose  
 L'elemento `Choose` contiene una serie di elementi `When` con attributi `Condition` che vengono sottoposti a test in ordine dall'alto verso il basso finché un elemento restituisce `true`. Se più di un elemento `When` restituisce `true`, viene usato solo il primo. Un elemento `Otherwise`, se presente, viene valutato se nessuna condizione per un elemento `When` restituisce `true`.  
  
 Gli elementi `Choose` possono essere usati come elementi figlio degli elementi `Project`, `When` e `Otherwise`. Gli elementi `When` e `Otherwise` possono avere elementi figlio `ItemGroup`, `PropertyGroup` o `Choose`.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa gli elementi `Choose` e `When` per l'elaborazione either/or. Le proprietà e gli elementi per il progetto vengono impostati in base al valore della proprietà `Configuration`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)