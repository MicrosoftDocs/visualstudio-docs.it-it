---
title: Destinazioni di MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f5b35c04d34143731ccf9fe5e8fe02f5389a2e5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-targets"></a>Destinazioni di MSBuild
Le destinazioni raggruppano le attività in un determinato ordine e consentono di suddividere il processo di compilazione in unità più piccole. Ad esempio, una destinazione può eliminare tutti i file presenti nella directory di output per preparare la compilazione, mentre un'altra compila gli input per il progetto e li inserisce nella directory vuota. Per altre informazioni sulle attività, vedere [Attività](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Dichiarazione delle destinazioni nel file di progetto  
 Per dichiarare le destinazioni in un file di progetto si usa l'elemento [Target](../msbuild/target-element-msbuild.md). Ad esempio, il codice XML seguente crea una destinazione denominata Construct che chiama l'attività Csc con il tipo di elemento Compile.  
  
```xml  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Come le proprietà di MSBuild, le destinazioni possono essere ridefinite. Ad esempio,  
  
```xml  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Se si esegue AfterBuild, viene visualizzato solo "Second occurrence".  
  
## <a name="target-build-order"></a>Ordine di compilazione delle destinazioni  
 Le destinazioni devono venire ordinate se l'input per una destinazione dipende dall'output di un'altra destinazione. Esistono diversi modi per specificare l'ordine di esecuzione delle destinazioni.  
  
-   Destinazioni iniziali  
  
-   Destinazioni predefinite  
  
-   Prima destinazione  
  
-   Dipendenze tra destinazioni  
  
-   `BeforeTargets` e `AfterTargets` (MSBuild 4.0)  
  
 Una destinazione non viene mai eseguita due volte durante una compilazione, anche se da essa dipende una destinazione successiva nella compilazione. Il contributo della destinazione alla compilazione termina dopo che è stata eseguita.  
  
 Per dettagli e altre informazioni sull'ordine di compilazione delle destinazioni, vedere [Ordine di compilazione delle destinazioni](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Suddivisione in batch della destinazione  
 Un elemento di destinazione può avere un attributo `Outputs` che specifica i metadati nel formato %(metadati). In questo caso MSBuild esegue la destinazione una volta per ogni valore univoco dei metadati, raggruppando o suddividendo in "batch" gli elementi che contengono quel valore dei metadati. Ad esempio,  
  
```xml  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 suddivide in batch gli elementi di riferimento in base ai metadati RequiredTargetFramework. L'output dell'esempio è simile al seguente:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 La suddivisione in batch della destinazione viene usata raramente nelle compilazioni reali. La suddivisione in batch delle attività è più comune. Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Compilazioni incrementali  
 Le compilazioni incrementali sono compilazioni ottimizzate in modo da non eseguire le destinazioni con file di output aggiornati rispetto ai file di input corrispondenti. Un elemento di destinazione può avere entrambi gli attributi `Inputs` e `Outputs` per indicare quali elementi la destinazione accetta come input e quali elementi genera come output.  
  
 Se tutti gli elementi di output sono aggiornati, MSBuild ignora la destinazione e questo migliora notevolmente la velocità di compilazione. Questa operazione è definita compilazione incrementale della destinazione. Se solo alcuni file sono aggiornati, MSBuild esegue la destinazione senza gli elementi aggiornati. Questa operazione è definita compilazione incrementale parziale della destinazione. Per altre informazioni, vedere [Compilazioni incrementali](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)