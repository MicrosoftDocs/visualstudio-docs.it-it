---
title: Creare un nuovo file di progetto MSBuild
description: Una procedura dettagliata per la creazione di un file di progetto MSBuild da zero per comprendere come è organizzato il codice XML e come è possibile modificarlo per controllare una compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3d0462382ddcc86a23c7e25162fb429b9f9893
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967540"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Procedura dettagliata: Creare un nuovo file di progetto MSBuild

I linguaggi di programmazione destinati a .NET Framework usano i file di progetto MSBuild per descrivere e controllare il processo di compilazione dell'applicazione. Quando si usa Visual Studio per creare un file di progetto MSBuild, il codice XML appropriato viene aggiunto automaticamente al file. Può tuttavia risultare utile comprendere l'organizzazione del codice XML e come è possibile modificarlo per controllare una compilazione.

 Per informazioni sulla creazione di un file di progetto per un progetto C++, vedere [MSBuild (c++)](/cpp/build/msbuild-visual-cpp).

 Questa procedura dettagliata mostra come creare in modo incrementale un file di progetto di base usando solo un editor di testo. I passaggi della procedura dettagliata sono i seguenti:

1. Estendere la variabile di ambiente PATH.

2. Creazione di un file di origine di applicazione minimo.

3. Creazione di un file di progetto MSBuild minimo.

4. Compilazione dell'applicazione tramite il file di progetto.

5. Aggiunta delle proprietà per controllare la compilazione.

6. Controllo della compilazione mediante la modifica dei valori delle proprietà.

7. Aggiunta delle destinazioni nella compilazione.

8. Controllo della compilazione specificando le destinazioni.

9. Compilazione incrementale.

Questa procedura dettagliata mostra come compilare il progetto tramite il prompt dei comandi ed esaminarne i risultati. Per altre informazioni su MSBuild e sulla sua esecuzione al prompt dei comandi, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).

Per completare la procedura dettagliata, è necessario che Visual Studio sia installato perché include MSBuild e il compilatore di Visual C#, necessari per la procedura dettagliata.

## <a name="extend-the-path"></a>Estendere il percorso

Prima di poter utilizzare MSBuild, è necessario estendere la variabile di ambiente PATH per includere tutti gli strumenti necessari. È possibile usare la **prompt dei comandi per gli sviluppatori per Visual Studio**. Cercarla in Windows 10 nella casella di ricerca della barra delle applicazioni di Windows. Per configurare l'ambiente in un prompt dei comandi comune o in un ambiente di scripting, eseguire *VSDevCmd.bat* nella sottocartella *Common7/Tools* di un'installazione di Visual Studio.

## <a name="create-a-minimal-application"></a>Creare un'applicazione minima

 Questa sezione illustra come creare un file di origine dell'applicazione C# minimo usando un editor di testo.

1. Al prompt dei comandi passare alla cartella in cui si desidera creare l'applicazione, ad esempio *\My Documents \\* o *\Desktop \\*.

2. Digitare **MD HelloWorld** per creare una sottocartella denominata *\HelloWorld \\*.

3. Digitare **cd HelloWorld** per passare alla nuova cartella.

4. Avviare il Blocco note o un altro editor di testo, quindi digitare il codice seguente.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. Salvare il file di codice sorgente e denominarlo *HelloWorld.cs*.

6. Compilare l'applicazione digitando **csc helloworld.cs** al prompt dei comandi.

7. Testare l'applicazione digitando **helloworld** al prompt dei comandi.

     Dovrebbe essere visualizzato il messaggio **Hello, world!** .

8. Eliminare l'applicazione digitando **del helloworld.exe** al prompt dei comandi.

## <a name="create-a-minimal-msbuild-project-file"></a>Creare un file di progetto MSBuild minimo

 Ora che si dispone di un file di origine di applicazione minimo, è possibile creare un file di progetto minimo per compilare l'applicazione. Questo file di progetto contiene gli elementi seguenti:

- Il nodo radice `Project` obbligatorio.

- Un nodo `ItemGroup` per contenere gli elementi Item.

- Un elemento Item che fa riferimento al file di origine dell'applicazione.

- Un nodo `Target` per contenere le attività necessarie per compilare l'applicazione.

- Un elemento `Task` per avviare il compilatore di Visual C# per compilare l'applicazione.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Per creare un file di progetto MSBuild minimo

1. Nell'editor di testo, sostituire il testo esistente con le due righe seguenti:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Inserire questo nodo `ItemGroup` come elemento figlio del nodo `Project`:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Si noti che questo nodo `ItemGroup` contiene già un elemento Item.

3. Aggiungere un nodo `Target` come elemento figlio del nodo `Project`. Denominare il nodo `Build`.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Inserire questo elemento Task come elemento figlio del nodo `Target`:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Salvare il file di progetto e denominarlo *HelloWorld. csproj*.

Il file di progetto minimo sarà simile al codice seguente:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Le attività nella destinazione Build vengono eseguite in sequenza. In questo caso, l'attività `Csc` del compilatore di Visual C# è l'unica attività. Questa attività deve ricevere un elenco di file di origine da compilare e tale elenco viene fornito dal valore dell'elemento `Compile`. L' `Compile` elemento fa riferimento a un solo file di origine, *HelloWorld.cs*.

> [!NOTE]
> Nell'elemento Item è possibile usare il carattere jolly asterisco ( \* ) per fare riferimento a tutti i file con estensione *CS* , come indicato di seguito:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="build-the-application"></a>Compilare l'applicazione

 A questo punto, usare il file di progetto appena creato per compilare l'applicazione.

1. Al prompt dei comandi digitare **msbuild helloworld. csproj-t:Build**.

     La destinazione Build del file di progetto Helloworld verrà compilata richiamando il compilatore di Visual C# per creare l'applicazione Helloworld.

2. Testare l'applicazione digitando **helloworld**.

     Dovrebbe essere visualizzato il messaggio **Hello, world!** .

> [!NOTE]
> Per visualizzare più dettagli sulla build, è possibile aumentare il livello di dettaglio. Per impostare il livello di dettaglio su "detailed", al prompt dei comandi digitare questo comando:
>
> **MSBuild HelloWorld. csproj-t:Build-livello di dettaglio: dettagliato**

## <a name="add-build-properties"></a>Aggiungere proprietà di compilazione

 Per aumentare il controllo della compilazione è possibile aggiungere proprietà di compilazione al file di progetto. Aggiungere le proprietà seguenti:

- Una proprietà `AssemblyName` per specificare il nome dell'applicazione.

- Una proprietà `OutputPath` per specificare la cartella contenente l'applicazione.

### <a name="to-add-build-properties"></a>Per aggiungere le proprietà di compilazione

1. Eliminare l'applicazione esistente digitando **del helloworld.exe** al prompt dei comandi.

2. Nel file di progetto, inserire l'elemento `PropertyGroup` subito dopo l'elemento `Project` di apertura:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Aggiungere questa attività alla destinazione Build subito prima dell'attività `Csc`:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     L'attività `MakeDir` crea una cartella con il nome specificato nella proprietà `OutputPath`, a condizione che al momento non esistano altre cartelle con lo stesso nome.

4. Aggiungere questo attributo `OutputAssembly` all'attività `Csc`:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     In questo modo il compilatore di Visual C# genera un assembly denominato dalla proprietà `AssemblyName` e lo inserisce nella cartella denominata dalla proprietà `OutputPath`.

5. Salvare le modifiche.

Il file di progetto sarà ora simile al codice seguente:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> Invece di aggiungere il delimitatore di percorso di barra rovesciata (\\) nell'attributo `OutputAssembly` dell'attività `Csc` è consigliabile aggiungerlo alla fine del nome della cartella quando la si specifica nell'elemento `OutputPath`. Quindi,
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly="$(OutputPath)$(AssemblyName).exe" />`
>
> è meglio di
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Testare le proprietà di compilazione

 Ora è possibile compilare l'applicazione tramite il file di progetto in cui sono state usate le proprietà di compilazione per specificare la cartella di output e il nome dell'applicazione.

1. Al prompt dei comandi digitare **msbuild helloworld. csproj-t:Build**.

     Questa operazione crea la cartella *\\ \bin* , quindi richiama il compilatore di Visual C# per creare l'applicazione *MSBuildSample* e la inserisce nella *cartella \\ \bin* .

2. Per verificare che la *cartella \\ \bin* sia stata creata e che contenga l'applicazione *MSBuildSample* , digitare **dir bin**.

3. Testare l'applicazione digitando **Bin\MSBuildSample**.

     Dovrebbe essere visualizzato il messaggio **Hello, world!** .

## <a name="add-build-targets"></a>Aggiungere destinazioni di compilazione

 A questo punto, aggiungere altre due destinazioni al file di progetto, come segue:

- Una destinazione Clean che elimina i file meno recenti.

- Una destinazione Rebuild che usa l'attributo `DependsOnTargets` per forzare l'esecuzione dell'attività Clean prima dell'attività Build.

Ora che sono presenti più destinazioni è possibile impostare la destinazione Build come destinazione predefinita.

### <a name="to-add-build-targets"></a>Per aggiungere destinazioni di compilazione

1. Nel file di progetto, aggiungere subito dopo la destinazione Build le due destinazioni seguenti:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     La destinazione Clean richiama l'attività Delete per eliminare l'applicazione. La destinazione Rebuild viene eseguita solo dopo l'esecuzione di entrambe le destinazioni Clean e Build. Anche se è priva di attività, la destinazione Rebuild comporta l'esecuzione della destinazione Clean prima della destinazione Build.

2. Aggiungere questo attributo `DefaultTargets` all'elemento `Project` di apertura:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     La destinazione Build viene impostata come destinazione predefinita.

Il file di progetto sarà ora simile al codice seguente:

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>Testare le destinazioni di compilazione

 È possibile usare le nuove destinazioni di compilazione per testare le funzionalità seguenti del file di progetto:

- Compilazione della build predefinita.

- Impostazione del nome dell'applicazione tramite il prompt dei comandi.

- Eliminazione dell'applicazione prima che venga compilata un'altra applicazione.

- Eliminazione dell'applicazione senza compilare un'altra applicazione.

### <a name="to-test-the-build-targets"></a>Per testare le destinazioni di compilazione

1. Al prompt dei comandi digitare **msbuild helloworld. csproj-p:AssemblyName = Greetings**.

     Poiché l'opzione **-t** non è stata usata per impostare in modo esplicito la destinazione, MSBuild esegue la destinazione di compilazione predefinita. L'opzione **-p** esegue l'override della `AssemblyName` proprietà e assegna al nuovo valore `Greetings` . Ciò comporta la creazione di una nuova applicazione, *Greetings.exe*, nella cartella *\bin \\* .

2. Per verificare che la *cartella \\ \bin* contenga sia l'applicazione *MSBuildSample* che la nuova applicazione *Greetings* , digitare **dir bin**.

3. Testare l'applicazione Greetings digitando **Bin\Greetings**.

     Dovrebbe essere visualizzato il messaggio **Hello, world!** .

4. Eliminare l'applicazione MSBuildSample digitando **msbuild helloworld. csproj-t:clean**.

     Viene eseguita l'attività Clean per rimuovere l'applicazione avente il valore predefinito della proprietà `AssemblyName`, ovvero `MSBuildSample`.

5. Eliminare l'applicazione Greetings digitando **msbuild helloworld. csproj-t:clean-p:AssemblyName = Greetings**.

     Viene eseguita l'attività Clean per rimuovere l'applicazione avente il valore specificato della proprietà **AssemblyName**, `Greetings`.

6. Per verificare che la *cartella \\ \bin* sia ora vuota, digitare **dir bin**.

7. Digitare **msbuild**.

     Sebbene non sia stato specificato un file di progetto, MSBuild compila il file *HelloWorld. csproj* poiché nella cartella corrente è presente un solo file di progetto. In questo modo l'applicazione *MSBuildSample* verrà creata nella cartella *\bin \\* .

     Per verificare che la *cartella \\ \bin* contenga l'applicazione *MSBuildSample* , digitare **dir bin**.

## <a name="build-incrementally"></a>Compilazione incrementale

 È possibile configurare MSBuild affinché compili una destinazione solo in caso di modifica dei file di origine o dei file di destinazione da cui la destinazione dipende. MSBuild usa il timestamp di un file per determinare se è stato modificato.

### <a name="to-build-incrementally"></a>Per eseguire la compilazione incrementale

1. Nel file di progetto, aggiungere alla destinazione di apertura Build gli attributi seguenti:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Questo specifica che la destinazione Build dipende dai file di input specificati nel gruppo di elementi `Compile` e che la destinazione di output è il file dell'applicazione.

     La destinazione Build risultante sarà simile al codice seguente:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Testare la destinazione di compilazione digitando **MSBuild-v:d** al prompt dei comandi.

     Tenere presente che *HelloWorld. csproj* è il file di progetto predefinito e che Build è la destinazione predefinita.

     L'opzione **-v:d** specifica una descrizione dettagliata del processo di compilazione.

     Verranno visualizzate le righe seguenti:

     **La destinazione "Build" verrà ignorata. Tutti i file di output sono aggiornati rispetto ai file di input.**

     **File di input: HelloWorld.cs**

     **File di output: BinMSBuildSample.exe**

     MSBuild ignora la destinazione Build perché nessuno dei file di origine è stato modificato dall'ultima compilazione dell'applicazione.

## <a name="c-example"></a>Esempio in C#

Nell'esempio seguente viene illustrato un file di progetto che compila un'applicazione C# e registra un messaggio contenente il nome del file di output.

### <a name="code"></a>Codice

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Esempio in Visual Basic

Nell'esempio seguente viene illustrato un file di progetto che compila un'applicazione Visual Basic e registra un messaggio contenente il nome del file di output.

### <a name="code"></a>Codice

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>Passaggi successivi

 Visual Studio è in grado di eseguire automaticamente molte delle operazioni descritte in questa procedura dettagliata. Per informazioni su come usare Visual Studio per creare, modificare, compilare e testare i file di progetto MSBuild, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Vedi anche

- [Panoramica di MSBuild](../msbuild/msbuild.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
