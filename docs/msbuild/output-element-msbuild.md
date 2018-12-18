---
title: Elemento Output (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e5f1d4dec10970770202e685860381cdec15608
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="output-element-msbuild"></a>Elemento Output (MSBuild)
Archivia i valori di output dell'attività in elementi e proprietà.  

 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  

## <a name="syntax"></a>Sintassi  

```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Descrizione|  
|---------------|-----------------|  
|`TaskParameter`|Attributo obbligatorio.<br /><br /> Nome del parametro di output dell'attività.|  
|`PropertyName`|È obbligatorio l'attributo `PropertyName` o l'attributo `ItemName`.<br /><br /> Proprietà che riceve il valore del parametro di output dell'attività. Il progetto può quindi fare riferimento alla proprietà con la sintassi `$(`*NomeProprietà*`)`. Questo nome di proprietà può essere il nome di una nuova proprietà o un nome già definito nel progetto.<br /><br /> Non è possibile usare questo attributo se si usa anche `ItemName`.|  
|`ItemName`|È obbligatorio l'attributo `PropertyName` o l'attributo `ItemName`.<br /><br /> Elemento che riceve il valore del parametro di output dell'attività. Il progetto può quindi fare riferimento all'elemento con la sintassi `@(`*NomeElemento*`)`. Il nome dell'elemento può essere il nome di un nuovo elemento o un nome già definito nel progetto.<br /><br /> Non è possibile usare questo attributo se si usa anche `PropertyName`.|  
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  

### <a name="parent-elements"></a>Elementi padre  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|Crea ed esegue un'istanza di un'attività di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="example"></a>Esempio  
 L'esempio di codice seguente mostra l'attività `Csc` eseguita all'interno di un elemento `Target`. Gli elementi e le proprietà passati ai parametri dell'attività vengono dichiarati al di fuori dell'ambito di questo esempio. Il valore dal parametro di output `OutputAssembly` viene archiviato nell'elemento `FinalAssemblyName` e il valore del parametro di output `BuildSucceeded` viene archiviato nella proprietà `BuildWorked`. Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md) (Attività).  

```xml  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)
