---
title: Trasformazioni di MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 670465059f86e7dd5ccbe725bc0d86aed2fc97b1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-transforms"></a>Trasformazioni di MSBuild
Una trasformazione è una conversione uno-a-uno di un elenco di elementi in un altro. Oltre a consentire a un progetto di convertire gli elenchi di elementi, una trasformazione consente a una destinazione di identificare un mapping diretto tra gli input e gli output. Questo argomento descrive le trasformazioni e il relativo uso in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per compilare progetti in modo più efficiente.  
  
## <a name="transform-modifiers"></a>Modificatori di comandi  
 Le trasformazioni non sono arbitrarie, ma sono limitate da una sintassi speciale in cui tutti i modificatori di trasformazione devono essere nel formato %(*NomeMetadatiElementi*). I metadati degli elementi possono essere usati come modificatori della trasformazione. Sono inclusi i metadati noti degli elementi, assegnati a ogni elemento al momento della creazione. Per un elenco di tutti i metadati noti degli elementi, vedere [Metadati noti degli elementi di MSBuild](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Nell'esempio seguente un elenco di file con estensione resx viene trasformato in un elenco di file con estensione resources. Il modificatore di trasformazione %(filename) specifica che ogni file con estensione resources ha lo stesso nome del file con estensione resx corrispondente.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  Per un elenco di elementi trasformato è possibile specificare un separatore personalizzato, in modo analogo a quanto accade con un elenco di elementi standard. Per separare, ad esempio, un elenco di elementi trasformato usando una virgola (,) anziché il punto e virgola predefinito (;), usare il codice XML seguente.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Se ad esempio gli elementi nell'elenco di elementi @(RESXFile) sono `Form1.resx`, `Form2.resx` e `Form3.resx`, gli output nell'elenco trasformato saranno `Form1.resources`, `Form2.resources` e `Form3.resources`.  
  
## <a name="using-multiple-modifiers"></a>Uso di più modificatori  
 Un'espressione di trasformazione può contenere più modificatori, che possono essere combinati in qualsiasi ordine e ripetuti. Nell'esempio seguente il nome della directory che contiene il file viene modificato, ma i file mantengono il nome e l'estensione originali.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Se ad esempio gli elementi contenuti nell'elenco di elementi `RESXFile` sono `Project1\Form1.resx`, `Project1\Form2.resx` e `Project1\Form3.text`, gli output nell'elenco trasformato saranno `Toolset\Form1.resx`, `Toolset\Form2.resx` e `Toolset\Form3.text`.  
  
## <a name="dependency-analysis"></a>Analisi delle dipendenze  
 Le trasformazioni garantiscono un mapping uno-a-uno tra l'elenco di elementi trasformato e l'elenco di elementi originale. Se pertanto una destinazione crea output che sono trasformazioni degli input, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può analizzare i timestamp degli input e output e decidere se ignorare, compilare o ricompilare parzialmente una destinazione.  
  
 Nell'[attività Copy](../msbuild/copy-task.md) dell'esempio seguente, ogni file dell'elenco di elementi `BuiltAssemblies` è associato a un file nella cartella di destinazione dell'attività, specificata mediante una trasformazione nell'attributo `Outputs`. Se viene modificato un file dell'elenco di elementi `BuiltAssemblies`, l'attività `Copy` verrà eseguita esclusivamente per il file modificato e tutti gli altri file verranno ignorati. Per altre informazioni sulle analisi delle dipendenze e su come usare le trasformazioni, vedere [Procedura: Eseguire la compilazione incrementale](../msbuild/how-to-build-incrementally.md).  
  
```xml  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 L'esempio seguente illustra un file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] in cui vengono usate le trasformazioni. In questo esempio si presuppone che vi sia un solo file con estensione xsd nella directory c:\sub0\sub1\sub2\sub3 e che la directory di lavoro sia c:\sub0.  
  
### <a name="code"></a>Codice  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Commenti  
 Questo esempio produce il seguente output:  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Procedura: Eseguire la compilazione incrementale](../msbuild/how-to-build-incrementally.md)