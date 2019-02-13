---
title: 'Procedura: Selezionare i file da compilare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2dad0c732a8f342e5c584202f810e1f53defb61e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798904"
---
# <a name="how-to-select-the-files-to-build"></a>Procedura: selezionare i file da compilare
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Quando si compila un progetto che contiene molti file, è possibile elencare separatamente ogni file nel file di progetto oppure è possibile usare caratteri jolly per includere tutti i file contenuti in una directory o in un set nidificato di directory.  
  
## <a name="specifying-inputs"></a>Specifica di input  
 Gli elementi rappresentano gli input di una compilazione. Per altre informazioni sugli elementi, vedere [Elementi](../msbuild/msbuild-items.md).  
  
 I file di una compilazione devono essere inclusi in un elenco di elementi nel file di progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. È possibile aggiungere più file agli elenchi di elementi includendoli uno alla volta o usando i caratteri jolly per includere molti file allo stesso tempo.  
  
#### <a name="to-declare-items-individually"></a>Per dichiarare gli elementi uno alla volta  
  
-   Usare gli attributi `Include` simili ai seguenti:  
  
     `<CSFile Include="form1.cs"/>`  
  
     - oppure -  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Se gli elementi di una raccolta di elementi non si trovano nella stessa directory del file di progetto, è necessario specificare il percorso completo o relativo dell'elemento. Ad esempio: `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>Per dichiarare più elementi  
  
-   Usare gli attributi `Include` simili ai seguenti:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     - oppure -  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specifying-inputs-with-wildcards"></a>Specifica di input con caratteri jolly  
 È anche possibile usare caratteri jolly per includere in modo ricorsivo tutti i file o solo file specifici dalle sottodirectory come input per una compilazione. Per altre informazioni sui caratteri jolly, vedere [Elementi](../msbuild/msbuild-items.md)  
  
 Gli esempi seguenti si basano su un progetto che contiene file grafici nelle directory e sottodirectory seguenti. Il file di progetto si trova nella directory Project:  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\Images\ImgJpgs\Img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Per includere tutti i file JPG della directory Images e delle relative sottodirectory  
  
-   Usare l'attributo `Include` seguente:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Per includere tutti i file JPG che iniziano con "img"  
  
-   Usare l'attributo `Include` seguente:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Per includere tutti i file delle directory, i cui nomi terminano con "jpgs"  
  
-   Usare uno degli attributi `Include` seguenti:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     - oppure -  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Passaggio di elementi a un'attività  
 In un file di progetto, è possibile usare la notazione @() nelle attività per specificare un intero elenco di elementi come input per una compilazione. È possibile usare questa notazione se si elencano tutti i file separatamente, altrimenti usare i caratteri jolly.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Per usare tutti i file Visual C# o Visual Basic come input  
  
-   Usare gli attributi `Include` simili ai seguenti:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     - oppure -  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  È necessario usare caratteri jolly con gli elementi per specificare gli input per una compilazione. Non è possibile specificare gli input tramite l'attributo `Sources` in attività di [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], ad esempio [Csc](../msbuild/csc-task.md) o [Vbc](../msbuild/vbc-task.md). L'esempio seguente non è valido in un file di progetto:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un progetto che include tutti i file di input separatamente.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente usa un carattere jolly per includere tutti i file con estensione CS.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Elementi](../msbuild/msbuild-items.md)
