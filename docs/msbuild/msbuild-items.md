---
title: Elementi MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d860d2d80cbb93c36a75c56a73895a401bc47660
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-items"></a>Elementi MSBuild
Gli elementi MSBuild sono input nel sistema di compilazione e in genere rappresentano i file. Gli elementi sono raggruppati in tipi di elemento in base ai nomi degli elementi. I tipi di elementi sono elenchi denominati di elementi che possono essere usati come parametri per le attività. Le attività usano i valori degli elementi per eseguire i passaggi del processo di compilazione.  
  
 Poiché gli elementi vengono denominati in base al tipo di elemento a cui appartengono, i termini "elemento" e "valore dell'elemento" sono interscambiabili.  
  
 **Contenuto dell'argomento**  
  
-   [Creazione di elementi in un file di progetto](#BKMK_Creating1)  
  
-   [Creazione di elementi durante l'esecuzione](#BKMK_Creating2)  
  
-   [Riferimento a elementi in un file di progetto](#BKMK_ReferencingItems)  
  
-   [Uso di caratteri jolly per specificare gli elementi](#BKMK_Wildcards)  
  
-   [Uso dell'attributo exclude](#BKMK_ExcludeAttribute)  
  
-   [Metadati degli elementi](#BKMK_ItemMetadata)  
  
    -   [Riferimento ai metadati degli elementi in un file di progetto](#BKMK_ReferencingItemMetadata)  
  
    -   [Metadati noti degli elementi](#BKMK_WellKnownItemMetadata)  
  
    -   [Trasformazione dei tipi di elemento tramite i metadati](#BKMK_Transforming)  
  
-   [Definizioni degli elementi](#BKMK_ItemDefinitions)  
  
-   [Attributi per gli elementi in un ItemGroup di una destinazione](#BKMK_AttributesWithinTargets)  
  
    -   [Rimuovere un attributo](#BKMK_RemoveAttribute)  
  
    -   [Attributo KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Attributo RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Attributo KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="BKMK_Creating1"></a> Creazione di elementi in un file di progetto  
 Si dichiarano gli elementi nel file di progetto come elementi figlio di un elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Il nome dell'elemento figlio è il tipo dell'elemento. L'attributo `Include` dell'elemento specifica gli elementi (i file) da includere con tale tipo di elemento. Ad esempio, il codice XML seguente crea un tipo di elemento denominato `Compile` che include due file.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 L'elemento "file2.cs" non sostituisce l'elemento "file1.cs", ma il nome file viene accodato all'elenco di valori per il tipo di elemento `Compile`. Non è possibile rimuovere un elemento da un tipo di elemento durante la fase di valutazione di una compilazione.  
  
 Il codice XML seguente crea lo stesso tipo di elemento dichiarando entrambi i file in un solo attributo `Include`. Si noti che i nomi file sono separati da punto e virgola.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="BKMK_Creating2"></a> Creazione di elementi durante l'esecuzione  
 Agli elementi non compresi in elementi [Target](../msbuild/target-element-msbuild.md) vengono assegnati valori durante la fase di valutazione di una compilazione. Durante la fase di esecuzione successiva, gli elementi possono essere creati o modificati nei modi seguenti:  
  
-   Le attività possono creare un elemento. Per creare un elemento, l'elemento [Task](../msbuild/task-element-msbuild.md) deve avere un elemento [Output](../msbuild/output-element-msbuild.md) figlio con un attributo `ItemName`.  
  
-   L'attività [CreateItem](../msbuild/createitem-task.md) può creare un elemento. Questo utilizzo è deprecato.  
  
-   A partire da .NET Framework 3.5, gli elementi `Target` possono contenere elementi [ItemGroup](../msbuild/itemgroup-element-msbuild.md) che possono contenere elementi Item.  
  
##  <a name="BKMK_ReferencingItems"></a> Riferimento a elementi in un file di progetto  
 Per fare riferimento ai tipi di elemento nel file di progetto viene usata la sintassi @(`ItemType`). Ad esempio, per fare riferimento al tipo di elemento nell'esempio precedente, si userà `@(Compile)`. Usando questa sintassi, è possibile passare gli elementi alle attività specificando il tipo di elemento come parametro di tale attività. Per altre informazioni, vedere [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).  
  
 Per impostazione predefinita, gli elementi di un tipo di elemento vengono separati da punto e virgola (;) quando viene espanso. È possibile usare la sintassi @(*ItemType*, '*separatore*') per specificare un separatore diverso da quello predefinito. Per altre informazioni, vedere [Procedura: Visualizzare un elenco di elementi separati da virgole](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="BKMK_Wildcards"></a> Uso di caratteri jolly per specificare gli elementi  
 È possibile usare i caratteri jolly **, \* e ? per specificare un gruppo di file come input per una compilazione invece di elencare ogni file separatamente.  
  
-   Il carattere jolly ? corrisponde a un singolo carattere.  
  
-   Il carattere jolly * corrisponde a zero o più caratteri.  
  
-   La sequenza di caratteri jolly ** corrisponde a un percorso parziale.  
  
 È possibile, ad esempio, specificare tutti i file CS nella directory che contiene il file di progetto usando l'elemento seguente nel file di progetto.  
  
```xml  
<CSFile Include="*.cs"/>  
```  
  
 L'elemento seguente seleziona tutti i file VB nell'unità D:  
  
```xml  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Per altre informazioni sui caratteri jolly, vedere [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="BKMK_ExcludeAttribute"></a> Uso dell'attributo exclude  
 Gli elementi Item possono contenere l'attributo `Exclude`, che esclude elementi (file) specifici dal tipo di elemento. L'attributo `Exclude` viene in genere usato con i caratteri jolly. Il codice XML seguente, ad esempio, aggiunge ogni file CS nella directory al tipo di elemento CSFile, tranne il file `DoNotBuild.cs`.  
  
```xml  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 L'attributo `Exclude` interessa solo gli elementi che vengono aggiunti dall'attributo `Include` nell'elemento item che li contiene entrambi. L'esempio seguente non escluderà il file Form1.cs, che è stato aggiunto nell'elemento item precedente.  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Per altre informazioni, vedere [Procedura: Escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="BKMK_ItemMetadata"></a> Metadati degli elementi  
 Gli elementi possono contenere metadati oltre alle informazioni negli attributi `Include` e `Exclude`. Questi metadati possono essere usati dalle attività che richiedono altre informazioni sugli elementi o per dividere in batch le attività e le destinazioni. Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).  
  
 I metadati sono una raccolta di coppie chiave-valore che vengono dichiarate nel file di progetto come elementi figlio di un elemento item. Il nome dell'elemento figlio è il nome dei metadati e il valore dell'elemento figlio è il valore dei metadati.  
  
 I metadati sono associati all'elemento item che li contiene. Il codice XML seguente, ad esempio, aggiunge i metadati `Culture` che hanno il valore `Fr` a entrambi gli elementi "one.cs" e "two.cs" del tipo di elemento CSFile.  
  
```xml  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Un elemento può avere zero o più valori di metadati. È possibile modificare i valori dei metadati in qualsiasi momento. Se si impostano i metadati su un valore vuoto, di fatto li si rimuove dalla compilazione.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Riferimento ai metadati degli elementi in un file di progetto  
 È possibile fare riferimento ai metadati di un elemento nel file di progetto usando la sintassi %(`ItemMetadataName`). In caso di ambiguità, è possibile qualificare un riferimento usando il nome del tipo di elemento. È ad esempio possibile specificare %(*ItemType.ItemMetaDataName*). L'esempio seguente usa i metadati Display per dividere in batch l'attività Message. Per altre informazioni su come usare i metadati di un elemento per la divisione in batch, vedere [Metadati degli elementi nell'esecuzione in batch delle attività](../msbuild/item-metadata-in-task-batching.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Metadati noti degli elementi  
 Quando un elemento viene aggiunto a un tipo di elemento, a tale elemento vengono assegnati alcuni metadati noti. Tutti gli elementi, ad esempio, hanno i metadati noti `%(Filename)`, il cui valore è il nome file dell'elemento. Per altre informazioni, vedere [Metadati noti degli elementi](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Trasformazione dei tipi di elemento tramite i metadati  
 È possibile trasformare gli elenchi di elementi in nuovi elenchi di elementi usando i metadati. È ad esempio possibile trasformare un tipo di elemento `CppFiles` con elementi che rappresentano file CPP in un elenco corrispondente di file OBJ usando l'espressione `@(CppFiles -> '%(Filename).obj')`.  
  
 Il codice seguente crea un tipo di elemento `CultureResource` che contiene copie di tutti gli elementi `EmbeddedResource` con i metadati `Culture`. Il valore dei metadati `Culture` diventa il valore dei nuovi metadati `CultureResource.TargetDirectory`.  
  
```xml  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Per altre informazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md).  
  
##  <a name="BKMK_ItemDefinitions"></a> Definizioni degli elementi  
 A partire da .NET Framework 3.5, è possibile aggiungere metadati predefiniti a qualsiasi tipo di elemento usando l'[elemento ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Come i metadati noti, i metadati predefiniti sono associati a tutti gli elementi del tipo di elemento specificato. È possibile eseguire l'override esplicito dei metadati predefiniti nella definizione di un elemento. Il codice XML seguente, ad esempio, assegna agli elementi `Compile` "one.cs" e "three.cs" i metadati `BuildDay` con il valore "Monday". Il codice assegna all'elemento "two.cs" i metadati `BuildDay` con il valore "Tuesday".  
  
```xml  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Per altre informazioni, vedere [Definizioni degli elementi](../msbuild/item-definitions.md).  
  
##  <a name="BKMK_AttributesWithinTargets"></a> Attributi per gli elementi in un ItemGroup di una destinazione  
 A partire da .NET Framework 3.5, gli elementi `Target` possono contenere elementi [ItemGroup](../msbuild/itemgroup-element-msbuild.md) che possono contenere elementi Item. Gli attributi in questa sezione sono validi quando vengono specificati per un elemento in un `ItemGroup` che si trova in una `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Rimuovere un attributo  
 Gli elementi in un `ItemGroup` di una destinazione possono contenere l'attributo `Remove`, che rimuove elementi (file) specifici dal tipo di elemento. Questo attributo è stato introdotto in .NET Framework 3.5.  
  
 L'esempio seguente rimuove ogni file con estensione config dal tipo di elemento Compile.  
  
```xml  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> Attributo KeepMetadata  
 Un elemento item, se viene generato in una destinazione, può contenere l'attributo `KeepMetadata`. Se questo attributo è specificato, solo i metadati specificati nell'elenco di nomi delimitati da punto e virgola verranno trasferiti dall'elemento di origine a quello di destinazione. Un valore vuoto per questo attributo equivale a non specificarlo. L'attributo `KeepMetadata` è stato introdotto in .NET Framework 4.5.  
  
 L'esempio seguente mostra come usare l'attributo `KeepMetadata`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="BKMK_RemoveMetadata"></a> Attributo RemoveMetadata  
 Un elemento item, se viene generato in una destinazione, può contenere l'attributo `RemoveMetadata`. Se questo attributo è specificato, tutti i metadati vengono trasferiti dall'elemento di origine all'elemento di destinazione, a eccezione dei metadati i cui nomi sono contenuti nell'elenco di nomi separati da punto e virgola. Un valore vuoto per questo attributo equivale a non specificarlo. L'attributo `RemoveMetadata` è stato introdotto in .NET Framework 4.5.  
  
 L'esempio seguente mostra come usare l'attributo `RemoveMetadata`.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="BKMK_KeepDuplicates"></a> Attributo KeepDuplicates  
 Un elemento item, se viene generato in una destinazione, può contenere l'attributo `KeepDuplicates`. `KeepDuplicates` è un attributo `Boolean` che specifica se un elemento deve essere aggiunto al gruppo di destinazione se l'elemento è un duplicato esatto di un elemento esistente.  
  
 Se l'elemento di origine e destinazione hanno lo stesso valore Include, ma metadati diversi, l'elemento viene aggiunto anche se `KeepDuplicates` è impostato su `false`. Un valore vuoto per questo attributo equivale a non specificarlo. L'attributo `KeepDuplicates` è stato introdotto in .NET Framework 4.5.  
  
 L'esempio seguente mostra come usare l'attributo `KeepDuplicates`.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)   
 [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md)   
 [Procedura: Escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Procedura: Visualizzare un elenco di elementi separati da virgole](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definizioni degli elementi](../msbuild/item-definitions.md)   
 [Suddivisione in batch](../msbuild/msbuild-batching.md)   
 [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)