---
title: Confronto di proprietà ed elementi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d2464acb75d8ea8a309d788aa95dc86b44d47e9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="comparing-properties-and-items"></a>Confronto di proprietà ed elementi
Le proprietà e gli elementi MSBuild vengono usati per passare informazioni ad attività, valutare condizioni e archiviare valori a cui poter fare riferimento nel file di progetto.  
  
-   Le proprietà sono coppie nome-valore. Per altre informazioni, vedere [MSBuild Properties](../msbuild/msbuild-properties.md) (Proprietà MSBuild).  
  
-   Gli elementi sono oggetti che rappresentano in genere i file. Agli oggetti elemento possono essere associate raccolte di metadati. I metadati sono coppie nome-valore. Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).  
  
## <a name="scalars-and-vectors"></a>Valori scalari e vettori  
 Poiché le proprietà MSBuild sono coppie nome-valore con un solo valore di stringa, sono spesso descritte come *valori scalari*. I tipi di elemento MSBuild sono invece elenchi di elementi e sono pertanto spesso descritti come *vettori*. In realtà le proprietà possono comunque rappresentare più valori, mentre i tipi di elemento possono non avere elementi o aver uno.  
  
### <a name="target-dependency-injection"></a>Inserimento delle dipendenze di destinazione  
 Per comprendere come le proprietà possono rappresentare più valori, considerare un modello di utilizzo comune per aggiungere una destinazione a un elenco di destinazioni da compilare. Questo elenco è in genere rappresentato da un valore della proprietà, con i nomi di destinazione separati da punti e virgola.  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 La proprietà `BuildDependsOn` viene in genere usata come argomento di un attributo di destinazione `DependsOnTargets` che lo converte in modo efficace in un elenco di elementi. Questa proprietà può essere sottoposta a override per aggiungere una destinazione o per modificare l'ordine di esecuzione della destinazione. Ad esempio,  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 La destinazione CustomBuild viene aggiunta all'elenco di destinazione, attribuendo `BuildDependsOn` al valore `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 A partire da MSBuild 4.0, l'inserimento delle dipendenze di destinazione è deprecato. Al suo posto usare gli attributi `AfterTargets` e `BeforeTargets`. Per altre informazioni, vedere [Target Build Order](../msbuild/target-build-order.md) (Ordine di compilazione delle destinazioni).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Conversioni fra stringhe ed elenchi di elementi  
 Se necessario MSBuild esegue la conversione da e in tipi di elemento e valori stringa. Per vedere come un elenco di elementi può diventare un valore stringa, considerare cosa succede quando un tipo di elemento viene usato come valore di una proprietà MSBuild:  
  
```xml  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 Il tipo di elemento OutputDir presenta un attributo `Include` con il valore "KeyFiles\\;Certificates\\". MSBuild analizza questa stringa suddividendola in due elementi, KeyFiles\ e Certificates\\. Quando il tipo di elemento OutputDir viene usato come valore della proprietà OutputDirList, MSBuild converte o "rende flat" il tipo di elemento nella stringa "KeyFiles\\;Certificates\\" con elementi separati da punto e virgola.  
  
## <a name="properties-and-items-in-tasks"></a>Proprietà ed elementi in attività  
 Le proprietà e gli elementi vengono usati come input e output nelle attività MSBuild. Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md) (Attività).  
  
 Le proprietà vengono passate alle attività sotto forma di attributi. All'interno dell'attività una proprietà MSBuild viene rappresentata da un tipo di proprietà il cui valore può essere convertito in e da una stringa. I tipi di proprietà supportati sono `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string` e qualsiasi altro tipo che <xref:System.Convert.ChangeType%2A> è in grado di gestire.  
  
 Gli elementi vengono passati alle attività come oggetti <xref:Microsoft.Build.Framework.ITaskItem>. All'interno dell'attività, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> rappresenta il valore dell'elemento e <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> recupera i relativi metadati.  
  
 È possibile passare l'elenco di elementi di un tipo di elemento sotto forma di matrice di oggetti `ITaskItem`. A partire da .NET Framework 3.5, gli elementi possono essere rimossi da un elenco di elementi in una destinazione usando l'attributo `Remove`. Poiché gli elementi possono essere rimossi da un elenco di elementi, è possibile che un tipo di elemento non contenta elementi. Se un elenco di elementi viene passato a un'attività, il codice dell'attività deve verificare questa possibilità.  
  
## <a name="property-and-item-evaluation-order"></a>Proprietà e ordine di valutazione degli elementi  
 Durante la fase di valutazione di una build, i file importati vengono incorporati nella build nell'ordine in cui vengono visualizzati. Le proprietà e gli elementi sono definiti in tre passaggi nell'ordine seguente:  
  
-   Le proprietà vengono definite e modificate nell'ordine in cui vengono visualizzate.  
  
-   Le definizioni dell'elemento vengono definite e modificate nell'ordine in cui vengono visualizzate.  
  
-   Gli elementi vengono definiti e modificati nell'ordine in cui vengono visualizzati.  
  
 Durante la fase di esecuzione di una build, le proprietà e gli elementi definiti all'interno di destinazioni vengono valutati insieme in un'unica fase nell'ordine in cui vengono visualizzati.  
  
 Non è tuttavia l'unico approccio. Quando si definisce una proprietà, una definizione dell'elemento o un elemento, viene valutato il relativo valore. L'analizzatore di espressioni espande la stringa che specifica il valore. L'espansione della stringa dipende dalla fase di compilazione. Di seguito viene riportato un ordine di valutazione di proprietà ed elementi più dettagliato:  
  
-   Durante la fase di valutazione di una build:  
  
    -   Le proprietà vengono definite e modificate nell'ordine in cui vengono visualizzate. Vengono eseguite le funzioni di proprietà. I valori di proprietà nel formato $(PropertyName) vengono espansi all'interno di espressioni. Il valore della proprietà viene impostato sull'espressione espansa.  
  
    -   Le definizioni dell'elemento vengono definite e modificate nell'ordine in cui vengono visualizzate. Le funzioni di proprietà sono già state espanse all'interno di espressioni. I valori di metadati vengono impostati sulle espressioni espanse.  
  
    -   I tipi di elemento vengono definiti e modificati nell'ordine in cui vengono visualizzati. I valori di elemento nel formato @(ItemType) vengono espansi. Anche le trasformazioni degli elementi vengono espanse. Le funzioni di proprietà e i valori sono già stati espansi all'interno di espressioni. L'elenco di elementi e i valori di metadati vengono impostati sulle espressioni espanse.  
  
-   Durante la fase di esecuzione di una build:  
  
    -   Le proprietà e gli elementi definiti all'interno di destinazione vengono valutati insieme nell'ordine in cui vengono visualizzati. Vengono eseguite le funzioni di proprietà e i valori della proprietà vengono espansi all'interno di espressioni. Anche i valori e le trasformazioni degli elementi vengono espansi. I valori di proprietà, i valori del tipo di elemento e i valori di metadati vengono impostati sulle espressioni espanse.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Effetti meno evidenti dell'ordine di valutazione  
 Nella fase di valutazione di una build la valutazione delle proprietà precede la valutazione degli elementi. È tuttavia possibile che le proprietà abbiano valori visualizzati che devono dipendere da valori elemento. Considerare lo script seguente.  
  
```xml  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Eseguendo l'attività Message viene visualizzato il messaggio seguente:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Infatti il valore di `KeyFileVersion` è la stringa "@(KeyFile->'%(Version)')". L'elemento e le trasformazioni dell'elemento non sono stati espansi quando la proprietà è stata definita. Alla proprietà `KeyFileVersion` è stato quindi assegnato il valore della stringa non espansa.  
  
 Durante la fase di esecuzione della build, nel corso dell'elaborazione dell'attività Message, MSBuild espande la stringa "@(KeyFile->'%(Version)')" per ottenere "1.0.0.3".  
  
 Si noti che lo stesso messaggio viene visualizzato anche se l'ordine dei gruppi di proprietà ed elementi è stato invertito.  
  
 Come secondo esempio considerare cosa può accadere quando i gruppi di proprietà ed elementi si trovano all'interno di destinazioni:  
  
```xml  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 L'attività Message visualizza il messaggio seguente:  
  
```  
KeyFileVersion:   
```  
  
 Durante la fase di esecuzione della build, i gruppi di proprietà ed elementi definiti all'interno di destinazioni vengono infatti valutati dall'alto verso il basso nello stesso momento. Quando viene definito `KeyFileVersion`, il valore `KeyFile` è sconosciuto. La trasformazione dell'elemento si espande quindi in una stringa vuota.  
  
 In questo caso, invertendo l'ordine dei gruppi di proprietà ed elemento è possibile ripristinare il messaggio originale:  
  
```xml  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Il valore di `KeyFileVersion` è impostato su "1.0.0.3" e non su "@(KeyFile->'%(Version)')". L'attività Message visualizza il messaggio seguente:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md) (Concetti avanzati)