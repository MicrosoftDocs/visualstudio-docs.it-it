---
title: Elemento Property (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e50a6dd66c2dca7fa4159c578ccd334ed1d26cae
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632953"
---
# <a name="property-element-msbuild"></a>Elemento Property (MSBuild)

Contiene un nome un valore della proprietà definiti dall'utente. Ogni proprietà utilizzata in un progetto MSBuild deve essere specificata come elemento figlio di un elemento `PropertyGroup`.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Sintassi

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elemento figlio

 Nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento di raggruppamento per le proprietà.|

## <a name="text-value"></a>Valore di testo

 Il valore di testo è facoltativo.

 Questo testo specifica il valore della proprietà e può contenere codice XML.

## <a name="remarks"></a>Note

 I nomi proprietà possono contenere solo caratteri ASCII. Per fare riferimento ai valori delle proprietà nel progetto, si inserisce il nome proprietà tra "`$(`" e "`)`". `$(builddir)\classes`, ad esempio, restituirà *build\classes*, se la proprietà `builddir` ha il valore `build`. Per altre informazioni sulle proprietà, vedere [Proprietà di MSBuild](../msbuild/msbuild-properties.md).

## <a name="example"></a>Esempio

 Il codice seguente imposta la proprietà `Optimization` su `false` e la proprietà `DefaultVersion` su `1.0` se la proprietà `Version` è vuota.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Vedere anche

- [Proprietà di MSBuild](../msbuild/msbuild-properties.md)
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
