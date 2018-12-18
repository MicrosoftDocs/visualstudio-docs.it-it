---
title: Attività CreateProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 817d888a14d20b4778b28f81811b876c6d97ad61
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="createproperty-task"></a>Attività CreateProperty
Popola le proprietà con i valori passati. In questo modo i valori vengono copiati da una proprietà o una stringa a un'altra.  
  
## <a name="attributes"></a>Attributi  
 Nella tabella che segue vengono descritti i parametri dell'attività `CreateProperty` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Value`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il valore da copiare nella nuova proprietà.|  
|`ValueSetByTask`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene lo stesso valore del parametro `Value`. Usare questo parametro solo quando si vuole evitare che la proprietà di output venga impostata da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] quando la destinazione di inclusione viene ignorata perché gli output sono aggiornati.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'attività `CreateProperty` per creare la proprietà `NewFile` usando la combinazione dei valori della proprietà `SourceFilename` e `SourceFileExtension`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Dopo l'esecuzione del progetto il valore della proprietà `NewFile` è `Module1.vb`.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)