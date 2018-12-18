---
title: 'Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cf71d7a62352e09e9024bef3f5d2c35b9c57b484
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="walkthrough-creating-an-msbuild-project-file-from-scratch"></a>Procedura dettagliata: creazione di un nuovo file di progetto MSBuild
I linguaggi di programmazione destinati a .NET Framework usano i file di progetto MSBuild per descrivere e controllare il processo di compilazione dell'applicazione. Quando si usa Visual Studio per creare un file di progetto MSBuild, il codice XML appropriato viene aggiunto automaticamente al file. Può tuttavia risultare utile comprendere l'organizzazione del codice XML e come è possibile modificarlo per controllare una compilazione.  
  
 Per informazioni sulla creazione di un file di progetto per un progetto C++, vedere [MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp).  
  
 Questa procedura dettagliata mostra come creare in modo incrementale un file di progetto di base usando solo un editor di testo. I passaggi della procedura dettagliata sono i seguenti:  
  
-   Creazione di un file di origine di applicazione minimo.  
  
-   Creazione di un file di progetto MSBuild minimo.  
  
-   Estensione della variabile di ambiente PATH per includere MSBuild.  
  
-   Compilazione dell'applicazione tramite il file di progetto.  
  
-   Aggiunta delle proprietà per controllare la compilazione.  
  
-   Controllo della compilazione mediante la modifica dei valori delle proprietà.  
  
-   Aggiunta delle destinazioni nella compilazione.  
  
-   Controllo della compilazione specificando le destinazioni.  
  
-   Compilazione incrementale.  
  
 Questa procedura dettagliata mostra come compilare il progetto tramite il prompt dei comandi ed esaminarne i risultati. Per altre informazioni su MSBuild e su come eseguirlo al prompt dei comandi, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 Per completare la procedura dettagliata sono necessari MSBuild e il compilatore di Visual C#, entrambi disponibili in .NET Framework (versione 2.0, 3.5, 4.0 o 4.5), che deve essere installato nel sistema in uso.  
  
## <a name="creating-a-minimal-application"></a>Creazione di un'applicazione minima  
 Questa sezione illustra come creare un file di origine di applicazione di Visual C# minimo tramite un editor di testo.  
  
#### <a name="to-create-the-minimal-application"></a>Per creare l'applicazione minima  
  
1.  Al prompt dei comandi, passare alla cartella in cui si vuole creare l'applicazione, ad esempio \Documenti\ o \Desktop\\.  
  
2.  Digitare **md HelloWorld** per creare una sottocartella denominata \HelloWorld\\.  
  
3.  Digitare **cd HelloWorld** per passare alla nuova cartella.  
  
4.  Avviare il Blocco note o un altro editor di testo, quindi digitare il codice seguente.  
  
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
  
5.  Salvare questo file di codice sorgente e denominarlo Helloworld.cs.  
  
6.  Compilare l'applicazione digitando **csc helloworld.cs** al prompt dei comandi.  
  
7.  Testare l'applicazione digitando **helloworld** al prompt dei comandi.  
  
     Dovrebbe essere visualizzato il messaggio **Hello, world!** .  
  
8.  Eliminare l'applicazione digitando **del helloworld.exe** al prompt dei comandi.  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>Creazione di un file di progetto MSBuild minimo  
 Ora che si dispone di un file di origine di applicazione minimo, è possibile creare un file di progetto minimo per compilare l'applicazione. Questo file di progetto contiene gli elementi seguenti:  
  
-   Il nodo radice `Project` obbligatorio.  
  
-   Un nodo `ItemGroup` per contenere gli elementi Item.  
  
-   Un elemento Item che fa riferimento al file di origine dell'applicazione.  
  
-   Un nodo `Target` per contenere le attività necessarie per compilare l'applicazione.  
  
-   Un elemento `Task` per avviare il compilatore di Visual C# per compilare l'applicazione.  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>Per creare un file di progetto MSBuild minimo  
  
1.  Nell'editor di testo, sostituire il testo esistente con le due righe seguenti:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  Inserire questo nodo `ItemGroup` come elemento figlio del nodo `Project`:  
  
    ```xml  
    <ItemGroup>  
      <Compile Include="helloworld.cs" />  
    </ItemGroup>  
    ```  
  
     Si noti che questo nodo `ItemGroup` contiene già un elemento Item.  
  
3.  Aggiungere un nodo `Target` come elemento figlio del nodo `Project`. Denominare il nodo `Build`.  
  
    ```xml  
    <Target Name="Build">  
    </Target>  
    ```  
  
4.  Inserire questo elemento Task come elemento figlio del nodo `Target`:  
  
    ```xml  
    <Csc Sources="@(Compile)"/>  
    ```  
  
5.  Salvare questo file di progetto e denominarlo Helloworld.csproj.  
  
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
  
 Le attività nella destinazione Build vengono eseguite in sequenza. In questo caso, l'attività `Csc` del compilatore di Visual C# è l'unica attività. Questa attività deve ricevere un elenco di file di origine da compilare e tale elenco viene fornito dal valore dell'elemento `Compile`. L'elemento `Compile` fa riferimento a un solo file di origine, Helloworld.cs.  
  
> [!NOTE]
>  Nell'elemento Item è possibile usare il carattere jolly asterisco (*) per fare riferimento a tutti i file che presentano l'estensione di file cs, come segue:  
>   
>  `<Compile Include="*.cs" />`  
>   
>  È però consigliabile evitare l'uso di caratteri jolly, perché, in caso di aggiunta o eliminazione di file di origine, rende più difficile il debug e l'indirizzamento selettivo.  
  
## <a name="extending-the-path-to-include-msbuild"></a>Estensione di Path per includere MSBuild  
 Prima di poter accedere a MSBuild è necessario estendere la variabile di ambiente PATH in modo che includa la cartella di .NET Framework.  
  
#### <a name="to-add-msbuild-to-your-path"></a>Per aggiungere MSBuild al percorso  
  
-   Aprire Visual Studio 2013 e individuare MSBuild.exe nella cartella MSBuild (`%ProgramFiles%\MSBuild` in un sistema operativo a 32 bit o `%ProgramFiles(x86)%\MSBuild` in un sistema operativo a 64 bit).  
  
     Al prompt dei comandi digitare **set PATH=%PATH%;%ProgramFiles%\MSBuild** o **set PATH=%PATH%;%ProgramFiles(x86)%\MSBuild**.  
  
     In alternativa, se è installato Visual Studio, è possibile usare il **prompt dei comandi di Visual Studio**, perché presenta una variabile PATH che include la cartella MSBuild.  
  
## <a name="using-the-project-file-to-build-the-application"></a>Uso del file di progetto per compilare l'applicazione  
 A questo punto, usare il file di progetto appena creato per compilare l'applicazione.  
  
#### <a name="to-build-the-application"></a>Per compilare l'applicazione  
  
1.  Al prompt dei comandi digitare **msbuild helloworld.csproj /t:Build**.  
  
     La destinazione Build del file di progetto Helloworld verrà compilata richiamando il compilatore di Visual C# per creare l'applicazione Helloworld.  
  
2.  Testare l'applicazione digitando **helloworld**.  
  
     Dovrebbe essere visualizzato il messaggio **Hello, world!** .  
  
> [!NOTE]
>  Per visualizzare più dettagli sulla build, è possibile aumentare il livello di dettaglio. Per impostare il livello di dettaglio su "detailed", digitare uno di questi comandi al prompt dei comandi:  
>   
>  **msbuild helloworld.csproj /t:Build /verbosity:detailed**  
  
## <a name="adding-build-properties"></a>Aggiunta di proprietà di compilazione  
 Per aumentare il controllo della compilazione è possibile aggiungere proprietà di compilazione al file di progetto. Aggiungere le proprietà seguenti:  
  
-   Una proprietà `AssemblyName` per specificare il nome dell'applicazione.  
  
-   Una proprietà `OutputPath` per specificare la cartella contenente l'applicazione.  
  
#### <a name="to-add-build-properties"></a>Per aggiungere le proprietà di compilazione  
  
1.  Eliminare l'applicazione esistente digitando **del helloworld.exe** al prompt dei comandi.  
  
2.  Nel file di progetto, inserire l'elemento `PropertyGroup` subito dopo l'elemento `Project` di apertura:  
  
    ```xml  
    <PropertyGroup>  
      <AssemblyName>MSBuildSample</AssemblyName>  
      <OutputPath>Bin\</OutputPath>  
    </PropertyGroup>  
    ```  
  
3.  Aggiungere questa attività alla destinazione Build subito prima dell'attività `Csc`:  
  
    ```xml  
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
    ```  
  
     L'attività `MakeDir` crea una cartella con il nome specificato nella proprietà `OutputPath`, a condizione che al momento non esistano altre cartelle con lo stesso nome.  
  
4.  Aggiungere questo attributo `OutputAssembly` all'attività `Csc`:  
  
    ```xml  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    ```  
  
     In questo modo il compilatore di Visual C# genera un assembly denominato dalla proprietà `AssemblyName` e lo inserisce nella cartella denominata dalla proprietà `OutputPath`.  
  
5.  Salvare le modifiche.  
  
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
>  Invece di aggiungere il delimitatore di percorso di barra rovesciata (\\) nell'attributo `OutputAssembly` dell'attività `Csc` è consigliabile aggiungerlo alla fine del nome della cartella quando la si specifica nell'elemento `OutputPath`. Quindi,  
>   
>  `<OutputPath>Bin\</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
>  è meglio di  
>   
>  `<OutputPath>Bin</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="testing-the-build-properties"></a>Test delle proprietà di compilazione  
 Ora è possibile compilare l'applicazione tramite il file di progetto in cui sono state usate le proprietà di compilazione per specificare la cartella di output e il nome dell'applicazione.  
  
#### <a name="to-test-the-build-properties"></a>Per testare le proprietà di compilazione  
  
1.  Al prompt dei comandi digitare **msbuild helloworld.csproj /t:Build**.  
  
     Questo comando crea la cartella \Bin\, quindi richiama il compilatore di Visual C# per creare l'applicazione MSBuildSample e la inserisce nella cartella \Bin\.  
  
2.  Per verificare che la cartella \Bin\ sia stata creata e che contenga l'applicazione MSBuildSample, digitare  **dir Bin**.  
  
3.  Testare l'applicazione digitando **Bin\MSBuildSample**.  
  
     Dovrebbe essere visualizzato il messaggio **Hello, world!** .  
  
## <a name="adding-build-targets"></a>Aggiunta di destinazioni di compilazione  
 A questo punto, aggiungere altre due destinazioni al file di progetto, come segue:  
  
-   Una destinazione Clean che elimina i file meno recenti.  
  
-   Una destinazione Rebuild che usa l'attributo `DependsOnTargets` per forzare l'esecuzione dell'attività Clean prima dell'attività Build.  
  
 Ora che sono presenti più destinazioni è possibile impostare la destinazione Build come destinazione predefinita.  
  
#### <a name="to-add-build-targets"></a>Per aggiungere destinazioni di compilazione  
  
1.  Nel file di progetto, aggiungere subito dopo la destinazione Build le due destinazioni seguenti:  
  
    ```xml  
    <Target Name="Clean" >  
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
    ```  
  
     La destinazione Clean richiama l'attività Delete per eliminare l'applicazione. La destinazione Rebuild viene eseguita solo dopo l'esecuzione di entrambe le destinazioni Clean e Build. Anche se è priva di attività, la destinazione Rebuild comporta l'esecuzione della destinazione Clean prima della destinazione Build.  
  
2.  Aggiungere questo attributo `DefaultTargets` all'elemento `Project` di apertura:  
  
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
  
## <a name="testing-the-build-targets"></a>Test delle destinazioni di compilazione  
 È possibile usare le nuove destinazioni di compilazione per testare le funzionalità seguenti del file di progetto:  
  
-   Compilazione della build predefinita.  
  
-   Impostazione del nome dell'applicazione tramite il prompt dei comandi.  
  
-   Eliminazione dell'applicazione prima che venga compilata un'altra applicazione.  
  
-   Eliminazione dell'applicazione senza compilare un'altra applicazione.  
  
#### <a name="to-test-the-build-targets"></a>Per testare le destinazioni di compilazione  
  
1.  Al prompt dei comandi digitare **msbuild helloworld.csproj /p:AssemblyName=Greetings**.  
  
     Poiché non è stata usata l'opzione **/t** per impostare in modo esplicito la destinazione, MSBuild esegue la destinazione predefinita Build. L'opzione **/p** esegue l'override della proprietà `AssemblyName` e le assegna il nuovo valore `Greetings`. In questo modo si crea una nuova applicazione denominata Greetings.exe nella cartella \Bin\.  
  
2.  Per verificare che la cartella \Bin\ contenga sia l'applicazione MSBuildSample che la nuova applicazione Greetings, digitare **dir Bin**.  
  
3.  Testare l'applicazione Greetings digitando **Bin\Greetings**.  
  
     Dovrebbe essere visualizzato il messaggio **Hello, world!** .  
  
4.  Eliminare l'applicazione MSBuildSample digitando **msbuild helloworld.csproj /t:clean**.  
  
     Viene eseguita l'attività Clean per rimuovere l'applicazione avente il valore predefinito della proprietà `AssemblyName`, ovvero `MSBuildSample`.  
  
5.  Eliminare l'applicazione Greetings digitando **msbuild helloworld.csproj /t:clean /p:AssemblyName=Greetings**.  
  
     Viene eseguita l'attività Clean per rimuovere l'applicazione avente il valore specificato della proprietà **AssemblyName**, `Greetings`.  
  
6.  Per verificare che la cartella \Bin\ sia vuota, digitare **dir Bin**.  
  
7.  Digitare **msbuild**.  
  
     Anche se non è stato specificato alcun file di progetto, MSBuild compila il file helloworld.csproj poiché nella cartella corrente esiste un solo file di progetto. Viene creata l'applicazione MSBuildSample nella cartella \Bin\.  
  
     Per verificare che la cartella \Bin\ contenga l'applicazione MSBuildSample, digitare **dir Bin**.  
  
## <a name="building-incrementally"></a>Compilazione incrementale  
 È possibile configurare MSBuild affinché compili una destinazione solo in caso di modifica dei file di origine o dei file di destinazione da cui la destinazione dipende. MSBuild usa il timestamp di un file per determinare se è stato modificato.  
  
#### <a name="to-build-incrementally"></a>Per eseguire la compilazione incrementale  
  
1.  Nel file di progetto, aggiungere alla destinazione di apertura Build gli attributi seguenti:  
  
    ```  
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
  
2.  Testare la destinazione Build digitando **msbuild /v:d** al prompt dei comandi.  
  
     Tenere presente che helloworld.csproj è il file di progetto predefinito e che Build è la destinazione predefinita.  
  
     L'opzione **/v:d** specifica che verrà fornita una descrizione dettagliata del processo di compilazione.  
  
     Verranno visualizzate le righe seguenti:  
  
     **La destinazione "Build" verrà ignorata. Tutti i file di output sono aggiornati rispetto ai file di input.**  
  
     **File di input: HelloWorld.cs**  
  
     **File di output: BinMSBuildSample.exe**  
  
     MSBuild ignora la destinazione Build perché nessuno dei file di origine è stato modificato dall'ultima compilazione dell'applicazione.  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 L'esempio seguente illustra un file di progetto che compila un'applicazione [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] e registra un messaggio contenente il nome del file di output.  
  
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
  
### <a name="comments"></a>Commenti  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 L'esempio seguente illustra un file di progetto che compila un'applicazione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e registra un messaggio contenente il nome del file di output.  
  
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
  
## <a name="whats-next"></a>Argomenti successivi  
 Visual Studio è in grado di eseguire automaticamente molte delle operazioni descritte in questa procedura dettagliata. Per imparare a usare Visual Studio per creare, modificare, compilare e verificare i file di progetto MSBuild, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="see-also"></a>Vedere anche  
[Panoramica di MSBuild](../msbuild/msbuild.md)  
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)