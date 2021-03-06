---
title: Attività XslTransformation | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività XslTransformation per trasformare un input XML usando un XSLT e l'output in un file o un dispositivo di output.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f779fc5d222fdd0985adef203f0bb20fc601a429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847946"
---
# <a name="xsltransformation-task"></a>XslTransformation (attività)

Consente di trasformare un input XML tramite un XSLT o un XSLT compilato e di creare un file o dispositivo di output.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `XslTransformation` .

|Parametro|Descrizione|
|---------------|-----------------|
|`OutputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di output per la trasformazione XML.|
|`Parameters`|Parametro `String` facoltativo.<br /><br /> Specifica i parametri per il documento di input XSLT.  Fornire il codice XML non elaborato che include ogni parametro come `<Parameter Name="" Value="" Namespace="" />` .|
|`XmlContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XML sotto forma di stringa.|
|`XmlInputPaths`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica i file di input XML.|
|`XslCompiledDllPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file XSLT compilato.|
|`XslContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XSLT sotto forma di stringa.|
|`XslInputPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file di input XSLT.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene utilizzato un file di trasformazione XSL *Transform. XSLT* per modificare il file XML `$(XmlInputFileName)` . Il codice XML trasformato viene scritto in `$(IntermediateOutputPath)output.xml` . La trasformazione XSL accetta `$(Parameter1)` come parametro di input.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Vedi anche

- [Parametri XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
