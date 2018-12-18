---
title: 'Procedura: Fare riferimento al nome o al percorso del file di progetto | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4d248727c5ebe54a86c2c006ca8bdd9342e208a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Procedura: fare riferimento al nome o al percorso del file di progetto
È possibile usare il nome o il percorso del progetto nel file di progetto senza dover creare una proprietà. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce proprietà riservate che fanno riferimento al nome file di progetto e altre proprietà relative al progetto. Per altre informazioni sulle proprietà riservate, vedere [Proprietà riservate e note di MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Uso della proprietà MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce alcune proprietà riservate che è possibile usare nei file di progetto senza definirle ogni volta. La proprietà riservata `MSBuildProjectName`, ad esempio, fornisce un riferimento al nome file di progetto.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Per usare la proprietà MSBuildProjectName  
  
-   Fare riferimento alla proprietà nel file di progetto con la notazione $(), come per qualsiasi altra proprietà. Ad esempio:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Uno dei vantaggi dell'uso di una proprietà riservata è che eventuali modifiche apportate al nome file di progetto vengono incorporate automaticamente. La volta successiva in cui si compila il progetto, il file di output assumerà il nuovo nome senza nessuna altra azione da parte dell'utente.  
  
> [!NOTE]
>  Le proprietà riservate non possono essere ridefinite nel file di progetto.  
  
## <a name="example"></a>Esempio  
 Il file di progetto di esempio seguente fa riferimento al nome del progetto come proprietà riservata per specificare il nome per l'output.  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
[MSBuild](../msbuild/msbuild.md)  
 [Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)