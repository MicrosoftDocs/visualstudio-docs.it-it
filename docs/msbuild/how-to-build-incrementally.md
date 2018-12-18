---
title: 'Procedura: Eseguire la compilazione incrementale | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fac1ce26c95d0a0c51c77e6ca1525d034a4e01f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-build-incrementally"></a>Procedura: eseguire la compilazione incrementale
Quando si compila un progetto di grandi dimensioni, è importante che i componenti compilati precedentemente e ancora aggiornati non vengano ricompilati. Se vengono ricompilate tutte le destinazioni, ogni compilazione impiegherà molto tempo. Per abilitare le compilazioni incrementali, in cui vengono compilate solo le destinazioni che non sono state compilate precedentemente o le destinazioni non aggiornate, [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) può confrontare i timestamp dei file di input con i timestamp dei file di output e stabilire se ignorare, compilare o ricompilare parzialmente una destinazione. Per questa operazione di confronto, è necessario un mapping uno a uno tra input e output. È possibile usare le trasformazioni per consentire alle destinazioni di identificare tale mapping diretto. Per altre informazioni sulle trasformazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Specifica di input e output  
 Una destinazione può essere compilata in modo incrementale se gli input e gli output sono specificati nel file di progetto.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Per specificare input e output per una destinazione  
  
-   Usare gli attributi `Inputs` e `Outputs` dell'elemento `Target`. Ad esempio:  
  
    ```xml  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può confrontare i timestamp dei file di input con i timestamps dei file di output e determinare se ignorare, compilare o ricompilare parzialmente una destinazione. Nell'esempio seguente, se un file dell'elenco di elementi `@(CSFile)` è più recente del file hello.exe, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] compilerà la destinazione; in caso contrario verrà ignorato:  
  
```xml  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Quando gli input e gli output sono specificati in una destinazione, ogni output può essere mappato solo a un input oppure potrebbe non esserci alcun mapping diretto tra gli output e gli input. Nell'[attività Csc](../msbuild/csc-task.md) precedente, ad esempio, l'output hello.exe non può essere mappato a un singolo input, ma dipende da tutti gli elementi.  
  
> [!NOTE]
>  Una destinazione senza mapping diretto tra input e output verrà sempre compilata con maggiore frequenza rispetto a una destinazione in cui ogni output corrisponde a un solo input perché [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non può determinare quali output debbano essere ricompilati se alcuni input sono stati modificati.  
  
 Le attività, in cui è possibile identificare un mapping diretto tra output e input, ad esempio l'[attività LC](../msbuild/lc-task.md), sono più adatte per le compilazioni incrementali, a differenza delle attività `Csc` e [Vbc](../msbuild/vbc-task.md), che producono un assembly di output da un numero di input.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usato un progetto che compila file della Guida per un ipotetico sistema di Guida. Il progetto converte i file di origine con estensione TXT in file CONTENT intermedi, che vengono quindi combinati con i file di metadati XML per generare il file con estensione HELP finale usato dal sistema di Guida. Il progetto usa le attività ipotetiche seguenti:  
  
-   `GenerateContentFiles`: converte file TXT in file CONTENT.  
  
-   `BuildHelp`: combina i file CONTENT e i file di metadati XML per compilare il file HELP finale.  
  
 Il progetto usa trasformazioni per creare un mapping uno a uno tra input e output nell'attività `GenerateContentFiles`. Per altre informazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md). L'elemento `Output` è impostato per usare automaticamente gli output dall'attività `GenerateContentFiles` come input per l'attività `BuildHelp`.  
  
 Questo file di progetto contiene le destinazioni `Convert` e `Build`. Le attività `GenerateContentFiles` e `BuildHelp` vengono inserite rispettivamente nelle destinazioni `Convert` e `Build` in modo che ogni destinazione possa essere compilata in modo incrementale. Tramite l'elemento `Output`, gli output dell'attività `GenerateContentFiles` vengono inseriti nell'elenco di elementi `ContentFile` dove possono essere usati come input per l'attività `BuildHelp`. L'uso dell'elemento `Output` in questo modo offre automaticamente gli output da un'attività come input per un'altra attività in modo che non sia necessario elencare manualmente i singoli elementi o elenchi di elementi in ogni attività.  
  
> [!NOTE]
>  Sebbene la destinazione `GenerateContentFiles` possa essere compilata in modo incrementale, tutti gli output di tale destinazione sono sempre necessari come input per la destinazione `BuildHelp`. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] offre automaticamente tutti gli output da una sola destinazione come input per un'altra destinazione quando si usa l'elemento `Output`.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFiles Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFiles)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Destinazioni](../msbuild/msbuild-targets.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Trasformazioni](../msbuild/msbuild-transforms.md)   
 [Attività Csc](../msbuild/csc-task.md)   
 [Attività Vbc](../msbuild/vbc-task.md)
