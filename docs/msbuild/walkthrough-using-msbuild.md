---
title: 'Procedura dettagliata: Uso di MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed4e6599fc55143789e35aad5fd4848904ae0c37
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-using-msbuild"></a>Procedura dettagliata: utilizzo di MSBuild
MSBuild è la piattaforma di compilazione per Microsoft e Visual Studio. Questa procedura dettagliata introduce i blocchi predefiniti di MSBuild e mostra come scrivere, modificare ed eseguire il debug di progetti MSBuild. Contenuto della procedura dettagliata:

-   Creazione e modifica di un file di progetto.

-   Come usare le proprietà di compilazione.

-   Come usare gli elementi di compilazione.

 È possibile eseguire MSBuild da Visual Studio o dalla finestra di comando. In questa procedura dettagliata si crea un file di progetto MSBuild in Visual Studio. Si modifica il file di progetto in Visual Studio e si usa una finestra di comando per compilare il progetto ed esaminare i risultati.

## <a name="creating-an-msbuild-project"></a>Creazione di un progetto MSBuild
 Il sistema dei progetti di Visual Studio si basa su MSBuild. Questo facilita la creazione di un nuovo file di progetto in Visual Studio. In questa sezione si crea un file di progetto Visual C#. È possibile scegliere di creare invece un file di progetto Visual Basic. Nel contesto di questa procedura dettagliata la differenza tra i due file di progetto è minima.

#### <a name="to-create-a-project-file"></a>Per creare un file di progetto

1.  Aprire Visual Studio.

2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3.  Nella finestra di dialogo **Nuovo progetto** selezionare il tipo di progetto Visual C# e quindi selezionare il modello **Windows Forms Application**. Nella casella **Nome** digitare `BuildApp`. Immettere un **percorso** per la soluzione, ad esempio `D:\`. Accettare le impostazioni predefinite per **Crea directory per soluzione** (selezionato), **Aggiungi al controllo del codice sorgente** (non selezionato) e **Nome soluzione** (`BuildApp`).

     Scegliere **OK** per creare il file di progetto.

## <a name="examining-the-project-file"></a>Analisi del file di progetto
 Nella sezione precedente è stato usato Visual Studio per creare un file di progetto Visual C#. Il file di progetto è rappresentato in **Esplora soluzioni** dal nodo del progetto denominato BuildApp. È possibile usare l'editor Visual Studio Code per esaminare il file di progetto.

#### <a name="to-examine-the-project-file"></a>Per esaminare il file di progetto

1.  In **Esplora soluzioni** fare clic sul nodo del progetto BuildApp.

2.  Nel browser **Proprietà** si noti che la proprietà **File di progetto** è BuildApp.csproj. Tutti i file di progetto vengono denominati con il suffisso "proj". Se è stato creato un progetto Visual Basic, il file di progetto sarà denominato BuildApp.vbproj.

3.  Fare clic con il pulsante destro del mouse sul nodo del progetto, quindi scegliere **Scarica progetto**.

4.  Fare ancora clic con il pulsante destro del mouse sul nodo del progetto, quindi scegliere **Modifica BuildApp.csproj**.

     Il file di progetto verrà visualizzato nell'editor del codice.

## <a name="targets-and-tasks"></a>Destinazioni e attività
I file di progetto sono file in formato XML con il nodo radice [Project](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

È necessario specificare lo spazio dei nomi xmlns nell'elemento Project. Se `ToolsVersion` è presente in un nuovo progetto, deve essere "15.0".

La compilazione di un'applicazione viene eseguita con gli elementi [Target](../msbuild/target-element-msbuild.md) e [Task](../msbuild/task-element-msbuild.md).

-   Un'attività è la più piccola unità di lavoro, in altre parole, l'"atom" di una compilazione. Le attività sono componenti eseguibili indipendenti che possono avere input e output. Attualmente nel file di progetto non sono presenti attività definite o a cui si fa riferimento. Le attività vengono aggiunte al file di progetto nelle sezioni seguenti. Per altre informazioni, vedere l'argomento [Attività](../msbuild/msbuild-tasks.md).

-   Una destinazione è una sequenza denominata di attività. Per altre informazioni, vedere l'argomento [Destinazioni](../msbuild/msbuild-targets.md).

La destinazione predefinita non è definita nel file di progetto. Viene invece specificata nei progetti importati. L'elemento [Import](../msbuild/import-element-msbuild.md) specifica i progetti importati. Ad esempio, in un progetto C#, la destinazione predefinita viene importata dal file Microsoft.CSharp.targets.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

I file importati vengono effettivamente inseriti nel file di progetto dove vi si fa riferimento.

> [!NOTE]
> Alcuni tipi di progetto, ad esempio .NET Core, usano uno schema semplificato con un attributo `Sdk` invece di `ToolsVersion`. Questi progetti includono importazioni implicite e valori diversi per gli attributi predefiniti.

MSBuild tiene traccia delle destinazioni di una compilazione e garantisce che ogni destinazione non venga compilata più di una volta.

## <a name="adding-a-target-and-a-task"></a>Aggiunta di una destinazione e di un'attività
 Aggiungere una destinazione al file di progetto. Aggiungere un'attività alla destinazione che visualizza un messaggio.

#### <a name="to-add-a-target-and-a-task"></a>Per aggiungere una destinazione e un'attività

1.  Aggiungere le righe seguenti al file di progetto, subito dopo l'istruzione Import:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

     Verrà creata una destinazione denominata HelloWorld. Si noti che è disponibile il supporto di IntelliSense durante la modifica del file di progetto.

2.  Aggiungere righe alla destinazione HelloWorld in modo che la sezione risultante sia simile alla seguente:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3.  Salvare il file di progetto.

 L'attività Message è una delle tante disponibili in MSBuild. Per un elenco completo delle attività disponibili e informazioni sull'uso, vedere [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md).

 L'attività Message accetta il valore stringa dell'attributo Text come input e lo visualizza nel dispositivo di output. La destinazione HelloWorld esegue l'attività Message due volte: prima per visualizzare "Hello" e quindi per visualizzare "World".

## <a name="building-the-target"></a>Compilazione della destinazione
 Eseguire MSBuild dal **prompt dei comandi di Visual Studio** per compilare la destinazione HelloWorld definita sopra. Usare le opzioni della riga di comando /target o /t per selezionare la destinazione.

> [!NOTE]
>  Nelle sezioni successive il **prompt dei comandi di Visual Studio** sarà chiamato **finestra di comando**.

#### <a name="to-build-the-target"></a>Per compilare la destinazione

1.  Fare clic su **Start**, quindi su **Tutti i programmi**. Individuare e fare clic sul **prompt dei comandi di Visual Studio** nella cartella **Strumenti di Visual Studio**.

2.  Dalla finestra di comando passare alla cartella contente il file di progetto, in questo caso D:\BuildApp\BuildApp.

3.  Eseguire msbuild con l'opzione di comando /t: HelloWorld. La destinazione HelloWorld verrà selezionata e compilata:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Esaminare l'output nella **finestra di comando**. Saranno visualizzate le due righe "Hello" e "World":

    ```
    Hello
    World
    ```

> [!NOTE]
>  Se invece si visualizza `The target "HelloWorld" does not exist in the project`, è probabile che si sia dimenticato di salvare il file di progetto nell'editor di codice. Salvare il file e riprovare.

 Alternando l'editor di codice e la finestra di comando, è possibile modificare il file di progetto e visualizzare velocemente i risultati.

## <a name="build-properties"></a>Proprietà di compilazione
 Le proprietà di compilazione sono coppie nome-valore che agevolano la compilazione. Diverse proprietà di compilazione sono già definite all'inizio del file di progetto:

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 Tutte le proprietà sono elementi figlio degli elementi PropertyGroup. Il nome della proprietà è il nome dell'elemento figlio e il valore della proprietà è l'elemento testo dell'elemento figlio. Ad esempio,

```xml
<TargetFrameworkVersion>v15.0</TargetFrameworkVersion>
```

 definisce la proprietà denominata TargetFrameworkVersion, assegnandole il valore stringa "v15.0".

 Compilare le proprietà possono essere ridefinite in qualsiasi momento. Se

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 viene visualizzato in un secondo momento nel file di progetto o in un file importato in un secondo momento nel file di progetto, TargetFrameworkVersion accetta il nuovo valore "v3.5".

## <a name="examining-a-property-value"></a>Esaminare un valore della proprietà
 Per ottenere il valore di una proprietà, usare la sintassi seguente, dove PropertyName è il nome della proprietà:

```
$(PropertyName)
```

 Usare questa sintassi per esaminare alcune delle proprietà nel file di progetto.

#### <a name="to-examine-a-property-value"></a>Per esaminare un valore della proprietà

1.  Nell'editor di codice sostituire la destinazione HelloWorld con questo codice:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

2.  Salvare il file di progetto.

3.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Esaminare l'output. Verranno visualizzate queste due righe (la versione di .NET Framework può variare):

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

> [!NOTE]
>  Se non si visualizzano queste righe, è probabile che si sia dimenticato di salvare il file di progetto nell'editor di codice. Salvare il file e riprovare.

### <a name="conditional-properties"></a>Proprietà condizionali
 Diverse proprietà, ad esempio Configuration, sono definite in modo condizionale, vale a dire che l'attributo Condition è presente nell'elemento della proprietà. Le proprietà condizionali vengono definite o ridefinite solo se la condizione restituisce "true". Si noti che alle proprietà non definite viene assegnato il valore predefinito di una stringa vuota. Ad esempio,

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 indica che, se la proprietà Configuration non è ancora stata definita, è necessario definirla e assegnarle il valore "Debug".

 Quasi tutti gli elementi di MSBuild possono avere un attributo Condition. Per altre informazioni sull'uso dell'attributo Condition, vedere [Condizioni](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Proprietà riservate
 In MSBuild alcuni nomi di proprietà sono riservati per archiviare le informazioni relative al file di progetto e ai file binari di MSBuild. MSBuildToolsPath è un esempio di proprietà riservata. Si fa riferimento alle proprietà riservate con la notazione $, come per qualsiasi altra proprietà. Per altre informazioni, vedere [Procedura: Fare riferimento al nome o al percorso del file di progetto](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) e [Proprietà riservate e note di MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Variabili di ambiente
 È possibile fare riferimento alle variabili di ambiente nei file di progetto come si fa riferimento alle proprietà di compilazione. Ad esempio, per usare la variabile di ambiente PATH nel file di progetto, usare $(Path). Se il progetto contiene una definizione di una proprietà con lo stesso nome di una variabile di ambiente, la proprietà nel progetto esegue l'override del valore della variabile di ambiente. Per altre informazioni, vedere [Procedura: Usare le variabili di ambiente in una compilazione](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="setting-properties-from-the-command-line"></a>Impostazione delle proprietà dalla riga di comando
 Le proprietà possono essere definite dalla riga di comando usando l'opzione della Proprietà /property o /p. I valori delle proprietà ricevuti dalla riga di comando eseguono l'override dei valori delle proprietà impostati nel file di progetto e nelle variabili di ambiente.

#### <a name="to-set-a-property-value-from-the-command-line"></a>Per impostare un valore della proprietà dalla riga di comando

1.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release
    ```

2.  Esaminare l'output. Dovrebbe essere visualizzata questa riga:

    ```
    Configuration is Release.
    ```

 MSBuild crea la proprietà Configuration e le assegna il valore "Release".

## <a name="special-characters"></a>Caratteri speciali
 Alcuni caratteri hanno un significato particolare nei file di progetto di MSBuild. Tra gli esempi di questi caratteri sono inclusi il punto e virgola (;) e l'asterisco (*). Per usare questi caratteri speciali come valori letterali in un file di progetto, è necessario specificarli usando la sintassi %xx, dove xx rappresenta il valore esadecimale ASCII del carattere.

 Modificare l'attività Message per visualizzare il valore della proprietà Configuration con i caratteri speciali per renderla più leggibile.

#### <a name="to-use-special-characters-in-the-message-task"></a>Per usare caratteri speciali nell'attività Message

1.  Nell'editor del codice sostituire entrambe le attività Message con questa riga:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

2.  Salvare il file di progetto.

3.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Esaminare l'output. Dovrebbe essere visualizzata questa riga:

    ```
    $(Configuration) is "Debug"
    ```

 Per altre informazioni, vedere [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Elementi di compilazione
 Un elemento è un'informazione, in genere un nome file, usata come input per il sistema di compilazione. Ad esempio, una raccolta di elementi che rappresentano file di origine potrebbe venire passata a un'attività denominata Compile per compilarli in un assembly.

 Tutti gli elementi sono elementi figlio degli elementi ItemGroup. Il nome dell'elemento è il nome dell'elemento figlio e il valore dell'elemento è il valore dell'attributo Include dell'elemento figlio. I valori degli elementi con lo stesso nome vengono raccolti in tipi di elemento con tale nome.  Ad esempio,

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 definisce un gruppo di elementi contenente due elementi. Il tipo di elemento Compile ha due valori: "Program.cs" e "Properties\AssemblyInfo.cs".

 Il codice seguente crea lo stesso tipo di elemento dichiarando entrambi i file in un attributo Include, separati da punto e virgola.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 Per altre informazioni, vedere [Items](../msbuild/msbuild-items.md) (Elementi).

> [!NOTE]
>  Percorsi dei file sono relativi alla cartella contenente il file di progetto MSBuild.

## <a name="examining-item-type-values"></a>Analisi dei valori di un tipo di elemento
 Per ottenere i valori di un tipo di elemento, usare la sintassi seguente, dove ItemType è il nome del tipo di elemento:

```
@(ItemType)
```

 Usare questa sintassi per esaminare il tipo di elemento Compile nel file di progetto.

#### <a name="to-examine-item-type-values"></a>Per esaminare i valori di un tipo di elemento

1.  Nell'editor di codice sostituire l'attività di destinazione HelloWorld con questo codice:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

2.  Salvare il file di progetto.

3.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Esaminare l'output. Dovrebbe essere visualizzata questa lunga riga:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

 I valori di un tipo di elemento sono separati da punto e virgola per impostazione predefinita.

 Per modificare il separatore di un tipo di elemento, usare la sintassi seguente, dove ItemType è il tipo di elemento e Separator è una stringa di uno o più caratteri di separazione:

```
@(ItemType, Separator)
```

 Modificare l'attività Message per usare ritorni a capo e avanzamenti riga (%0A%0D) per visualizzare un elemento Compile per riga.

#### <a name="to-display-item-type-values-one-per-line"></a>Per visualizzare i valori di un tipo di elemento uno per riga

1.  Nell'editor del codice sostituire l'attività Message con questa riga:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2.  Salvare il file di progetto.

3.  Dalla **finestra di comando** immettere ed eseguire questa riga:

     `msbuild buildapp.csproj /t:HelloWorld`

4.  Esaminare l'output. Dovrebbero essere visualizzate queste righe:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Include, Exclude e caratteri jolly
 È possibile usare i caratteri jolly "*", "\*\*" e "?" con l'attributo Include per aggiungere elementi a un tipo di elemento. Ad esempio,

```xml
<Photos Include="images\*.jpeg" />
```

 aggiunge tutti i file con estensione ".jpeg" nella cartella images al tipo di elemento Photos, mentre

```xml
<Photos Include="images\**.jpeg" />
```

 aggiunge tutti i file con estensione ".jpeg" nella cartella images e in tutte le sottocartelle al tipo di elemento Photos. Per altri esempi, vedere [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).

 Si noti che gli elementi, quando vengono dichiarati, vengono aggiunti al tipo di elemento. Ad esempio,

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 crea un tipo di elemento denominato Photo contenente tutti i file nella cartella image con estensione ".jpeg" o ".gif". Il codice equivale alla riga seguente:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 È possibile escludere un elemento da un tipo di elemento con l'attributo Exclude. Di seguito è riportato un esempio:

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 aggiunge tutti i file con estensione ".cs" al tipo di elemento Compile, tranne i file i cui nomi contengono la stringa "Designer". Per altri esempi, vedere [Procedura: Escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md).

 L'attributo Exclude interessa solo gli elementi aggiunti dall'attributo Include nell'elemento item che li contiene entrambi. Ad esempio,

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 non escluderà il file Form1.cs, che è stato aggiunto nell'elemento item precedente.

##### <a name="to-include-and-exclude-items"></a>Per includere ed escludere elementi

1.  Nell'editor del codice sostituire l'attività Message con questa riga:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2.  Aggiungere questo gruppo di elementi immediatamente dopo l'elemento Import:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3.  Salvare il file di progetto.

4.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

5.  Esaminare l'output. Dovrebbe essere visualizzata questa riga:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadati degli elementi
 Gli elementi possono contenere metadati oltre alle informazioni raccolte dagli attributi Include ed Exclude. Questi metadati possono essere usati dalle attività che richiedono altre informazioni sugli elementi oltre al valore dell'elemento.

 Per dichiarare i metadati degli elementi nel file di progetto, è necessario creare un elemento con il nome dei metadati come elemento figlio dell'elemento. Un elemento può avere zero o più valori di metadati. Ad esempio, l'elemento CSFile seguente contiene metadati Culture con il valore "Fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Per ottenere il valore dei metadati di un tipo di elemento, usare la sintassi seguente, dove ItemType è il nome del tipo di elemento e MetaDataName è il nome dei metadati:

```
%(ItemType.MetaDataName)
```

#### <a name="to-examine-item-metadata"></a>Per esaminare i metadati di un elemento

1.  Nell'editor del codice sostituire l'attività Message con questa riga:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2.  Salvare il file di progetto.

3.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Esaminare l'output. Dovrebbero essere visualizzate queste righe:

    ```
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

 Si noti come la frase "Compile.DependentUpon" venga visualizzata più volte. L'uso di metadati con questa sintassi in una destinazione causa la "divisione in batch". Con la divisione in batch le attività nella destinazione vengono eseguite una volta per ogni valore di metadati univoco. Questo script di MSBuild è l'equivalente del comune costrutto di programmazione "for loop". Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Metadati noti
 Quando un elemento viene aggiunto a un elenco di elementi, a tale elemento vengono assegnati alcuni metadati noti. Ad esempio, %(FileName) restituisce il nome file di qualsiasi elemento. Per un elenco completo di metadati noti, vedere [Metadati noti degli elementi](../msbuild/msbuild-well-known-item-metadata.md).

##### <a name="to-examine-well-known-metadata"></a>Per esaminare i metadati noti

1.  Nell'editor del codice sostituire l'attività Message con questa riga:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2.  Salvare il file di progetto.

3.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Esaminare l'output. Dovrebbero essere visualizzate queste righe:

    ```
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

 Confrontando i due esempi sopra, è possibile osservare che, mentre non tutti gli elementi nel tipo di elemento Compile hanno i metadati DependentUpon, tutti gli elementi hanno i metadati Filename noti.

### <a name="metadata-transformations"></a>Trasformazioni di metadati
 Gli elenchi di elementi possono essere trasformati in nuovi elenchi di elementi. Per trasformare un elenco di elementi, usare la sintassi seguente, dove ItemType è il nome del tipo di elemento e MetadataName è il nome dei metadati:

```
@(ItemType -> '%(MetadataName)')
```

 Ad esempio, un elenco di file di origine può essere trasformato in una raccolta di file oggetto usando un'espressione come `@(SourceFiles -> '%(Filename).obj')`. Per altre informazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md).

##### <a name="to-transform-items-using-metadata"></a>Per trasformare gli elementi usando i metadati

1.  Nell'editor del codice sostituire l'attività Message con questa riga:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2.  Salvare il file di progetto.

3.  Dalla **finestra di comando** immettere ed eseguire questa riga:

    ```
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Esaminare l'output. Dovrebbe essere visualizzata questa riga:

    ```
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

 Si noti che i metadati espressi in questa sintassi non causano la divisione in batch.

## <a name="whats-next"></a>Argomenti successivi
 Per informazioni su come creare un file di progetto semplice passaggio per passaggio, vedere [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica di MSBuild](../msbuild/msbuild.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
