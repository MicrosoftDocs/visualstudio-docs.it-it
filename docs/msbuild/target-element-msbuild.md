---
title: Elemento Target (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c5d60d41c7c7866ed396a90eacec4ba61a05238
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="target-element-msbuild"></a>Elemento Target (MSBuild)
Contiene un set di attività da eseguire in sequenza in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<Target>  

## <a name="syntax"></a>Sintassi  

```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <OnError... />  
</Target>  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Attributo obbligatorio.<br /><br /> Nome della destinazione.|  
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare. Se la condizione restituisce `false`, la destinazione non eseguirà il corpo della destinazione o di eventuali destinazioni impostate nell'attributo `DependsOnTargets`. Per altre informazioni sulle condizioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Attributo facoltativo.<br /><br /> File che costituiscono gli input in questa destinazione. Per specificare più file, usare il punto e virgola come delimitatore. I timestamp dei file verranno confrontati con i timestamp dei file in `Outputs` per determinare se `Target` è aggiornata. Per altre informazioni, vedere [Compilazioni incrementali](../msbuild/incremental-builds.md), [Procedura: Eseguire la compilazione incrementale](../msbuild/how-to-build-incrementally.md) e [Trasformazioni](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Attributo facoltativo.<br /><br /> File che costituiscono gli output in questa destinazione. Per specificare più file, usare il punto e virgola come delimitatore. I timestamp dei file verranno confrontati con i timestamp dei file in `Inputs` per determinare se `Target` è aggiornata. Per altre informazioni, vedere [Compilazioni incrementali](../msbuild/incremental-builds.md), [Procedura: Eseguire la compilazione incrementale](../msbuild/how-to-build-incrementally.md) e [Trasformazioni](../msbuild/msbuild-transforms.md).|  
|`Returns`|Attributo facoltativo.<br /><br /> Set di elementi che saranno disponibili per le attività che richiamano questa destinazione, ad esempio, le attività di MSBuild. Se si specificano più destinazioni, usare il punto e virgola per separarle. Se le destinazioni nel file non hanno attributi `Returns`, in alternativa vengono usati gli attributi Outputs a questo scopo.|  
|`KeepDuplicateOutputs`|Attributo booleano facoltativo.<br /><br /> Se `true`, vengono registrati più riferimenti allo stesso elemento negli attributi Returns della destinazione.  Per impostazione predefinita, questo attributo è `false`.|  
|`BeforeTargets`|Attributo facoltativo.<br /><br /> Elenco di nomi di destinazione delimitato a punti e virgola.  Se specificato, indica che questa destinazione deve essere eseguita prima della destinazione o delle destinazioni specificate. Ciò consente all'autore del progetto di estendere un set di destinazioni esistente senza modificarle direttamente. Per altre informazioni, vedere [Ordine di compilazione delle destinazioni](../msbuild/target-build-order.md).|  
|`AfterTargets`|Attributo facoltativo.<br /><br /> Elenco di nomi di destinazione delimitato a punti e virgola. Se specificato, indica che questa destinazione deve essere eseguita dopo la destinazione o le destinazioni specificate. Ciò consente all'autore del progetto di estendere un set di destinazioni esistente senza modificarle direttamente. Per altre informazioni, vedere [Ordine di compilazione delle destinazioni](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Attributo facoltativo.<br /><br /> Destinazioni che devono essere eseguite prima che possa essere eseguita questa destinazione o un'analisi delle dipendenze di primo livello. Se si specificano più destinazioni, usare il punto e virgola per separarle.|  
|`Label`|Attributo facoltativo.<br /><br /> Identificatore che può identificare o ordinare elementi di sistema e utente.|  

### <a name="child-elements"></a>Elementi figlio  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|Crea ed esegue un'istanza di un'attività di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Possono esistere zero o più attività in una destinazione.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Contiene un set di elementi `Property` definiti dall'utente. A partire da .NET Framework 3.5, un elemento `Target` può contenere elementi `PropertyGroup`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Contiene un set di elementi `Item` definiti dall'utente. A partire da .NET Framework 3.5, un elemento `Target` può contenere elementi `ItemGroup`. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Fa in modo che venga eseguita una o più destinazioni se l'attributo `ContinueOnError` è ErrorAndStop (o `false`) per un'attività non riuscita. Possono esistere zero o più elementi `OnError` in una destinazione. Se sono presenti elementi `OnError`, devono essere gli ultimi elementi nell'elemento `Target`.<br /><br /> Per altre informazioni sull'attributo `ContinueOnError`, vedere [Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md).|  

### <a name="parent-elements"></a>Elementi padre  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="remarks"></a>Note  
 La prima destinazione da eseguire viene specificata in fase di esecuzione. Le destinazioni possono avere dipendenze da altre destinazioni. Ad esempio, una destinazione per la distribuzione dipende da una destinazione per la compilazione. Il motore [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] esegue le dipendenze nell'ordine in cui vengono visualizzate nell'attributo `DependsOnTargets`, da sinistra a destra. Per altre informazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).  

 Una destinazione viene eseguita una sola volta durante una compilazione, anche se ne dipende più di una destinazione.  

 Se una destinazione viene ignorata perché l'attributo `Condition` restituisce `false`, può ugualmente essere eseguita anche se viene richiamata in seguito nella compilazione e l'attributo `Condition` a quel punto restituisce `true`.  

 Prima di MSBuild 4, `Target` restituiva gli eventuali elementi specificati nell'attributo `Outputs`.  A questo scopo, MSBuild doveva registrare questi elementi nell'eventualità che le attività li richiedessero in un secondo momento durante la compilazione. Poiché non era possibile indicare le destinazioni con output che i chiamanti avrebbero richiesto, MSBuild accumulava tutti gli elementi da tutti gli `Outputs` in tutte le `Target` richiamate. Ciò causa problemi di ridimensionamento per le compilazioni con un numero elevato di elementi di output.  

 Se l'utente specifica `Returns` in un elemento `Target` in un progetto, solo le `Target` con un attributo `Returns` registrano tali elementi.  

 `Target` può contenere sia un attributo `Outputs` che un attributo `Returns`.  `Outputs` viene usato con `Inputs` per determinare se la destinazione è aggiornata. `Returns`, se presente, esegue l'override del valore di `Outputs` per determinare quali elementi vengono restituiti ai chiamanti.  Se `Returns` non è presente, `Outputs` sarà disponibile per i chiamanti tranne nel caso descritto prima.  

 Prima di MSBuild 4, ogni volta che `Target` includeva più riferimenti allo stesso elemento in `Outputs`, tali elementi duplicati venivano registrati. Nelle compilazioni di grandi dimensioni con un numero elevato di output e più interdipendenze tra progetti, veniva sprecata una grande quantità di memoria perché gli elementi duplicati non erano di alcuna utilità. Quando l'attributo `KeepDuplicateOutputs` viene impostato su `true`, questi duplicati vengono registrati.  

## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un elemento `Target` che esegue l'attività `Csc`.  

```xml  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Vedere anche  
 [Destinazioni](../msbuild/msbuild-targets.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
