---
title: Personalizzazione dell'analisi code coverage in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 54536e5e59f52a4051c715e5dc385672dc22721e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="customize-code-coverage-analysis"></a>Personalizzare l'analisi code coverage

Per impostazione predefinita, lo strumento per il code coverage di Visual Studio analizza tutti gli assembly della soluzione caricati durante gli unit test. È consigliabile mantenere questa impostazione predefinita in quanto funziona bene nella maggior parte dei casi. Per altre informazioni, vedere [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Prima di personalizzare il comportamento del code coverage, considerare alcune alternative:

- *Si vuole escludere il codice di test dai risultati del code coverage e includere solo il codice dell'applicazione.*

     Aggiungere `ExcludeFromCodeCoverage Attribute` alla classe di test.

- *Si vogliono includere assembly che non fanno parte della soluzione.*

     Ottenere i file con estensione pdb per questi assembly e copiarli nella stessa cartella dei file con estensione dll dell'assembly.

Per personalizzare il comportamento del code coverage, copiare l'[esempio alla fine di questo argomento](#sample) e aggiungerlo alla soluzione tramite il file con estensione *runsettings*. Modificarlo secondo le proprie esigenze e quindi nel menu **Test** scegliere **Impostazioni test** e **Seleziona file di impostazioni test**. Nella parte restante dell'articolo questa procedura viene descritta più nel dettaglio.

## <a name="the-run-settings-file"></a>File di impostazioni esecuzione test

Le impostazioni avanzate di code coverage vengono specificate in un file con estensione *runsettings*. Si tratta del file di configurazione usato dagli strumenti di testing unità. Si consiglia di copiare l'[esempio alla fine di questo argomento](#sample) e di modificarlo in base alle proprie esigenze.

Per personalizzare il code coverage, aggiungere un file di impostazioni esecuzione test alla soluzione:

1. Aggiungere un file XML come elemento della soluzione con l'estensione *runsettings*:

     In Esplora soluzioni scegliere **Aggiungi** > **Nuovo elemento** dal menu di scelta rapida della soluzione e selezionare **File XML**. Salvare il file con un nome che termina come *CodeCoverage.runsettings*.

2. Aggiungere il contenuto specificato nell'esempio alla fine di questo articolo, quindi personalizzarlo secondo le proprie esigenze come descritto nelle sezioni seguenti.

3. Nel menu **Test** scegliere **Impostazioni test** > **Seleziona file di impostazioni test** e selezionare il file.

4. A questo punto, quando si esegue **Analizza code coverage**, il file di impostazioni esecuzione test controllerà il comportamento. Ricordarsi che è necessario eseguire nuovamente il code coverage. I risultati e la colorazione del code coverage precedenti non vengono nascosti automaticamente quando si eseguono i test o si aggiorna il codice.

5. Per attivare e disattivare le impostazioni personalizzate, deselezionare o selezionare il file nel menu **Test** > **Impostazioni test**.

 ![Menu Impostazioni test con file di impostazioni personalizzato](../test/media/codecoverage-settingsfile.png)

Altri aspetti degli unit test possono essere configurati nello stesso file di impostazioni esecuzione test. Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).

### <a name="specifying-symbol-search-paths"></a>Specifica dei percorsi di ricerca dei simboli

Il code coverage richiede che siano presenti i simboli (file con estensione pdb) per gli assembly. Per gli assembly compilati dalla soluzione, i file di simboli sono solitamente presenti accanto ai file binari e il code coverage viene eseguito automaticamente. In alcuni casi invece è consigliabile includere assembly a cui si fa riferimento nell'analisi del code coverage. In tali casi, i file con estensione pdb non possono essere adiacenti ai binari, ma è possibile specificare il percorso di ricerca dei simboli nel file con estensione runsettings.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!WARNING]
> La risoluzione dei simboli può richiedere tempo, in particolare quando si usa un percorso file remoto con molti assembly. Di conseguenza, si consiglia di copiare i file remoti con estensione pdb nello stesso percorso locale dei file binari (.dll ed .exe).

### <a name="excluding-and-including"></a>Esclusione ed inclusione

È possibile escludere gli assembly specificati dall'analisi code coverage. Ad esempio:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

In alternativa, è possibile specificare gli assembly che devono essere inclusi. Questo approccio presenta lo svantaggio che quando si aggiungono più assembly alla soluzione, è necessario tenere a mente che occorre aggiungerli anche all'elenco:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Se `<Include>` è vuoto, l'elaborazione del code coverage include tutti gli assembly caricati, in cui è possibile trovare file con estensione pdb. Il code coverage non include gli elementi che corrispondono a una clausola in un elenco `<Exclude>`.

`Include` viene elaborato prima `Exclude`.

### <a name="regular-expressions"></a>Espressioni regolari

Includere ed escludere i nodi che usano le espressioni regolari. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Le espressioni regolari non equivalgono ai caratteri jolly. In particolare:

- **.\*** corrisponde a una stringa composta da qualsiasi carattere

- **\\.** corrisponde a un punto "."

- **\\(   \\)** corrisponde alle parentesi "(  )"

- **\\\\** corrisponde al delimitatore del percorso di file "\\"

- **^** corrisponde all'inizio della stringa

- **$** corrisponde alla fine della stringa

Tutte le corrispondenze fanno distinzione tra maiuscole e minuscole.

Ad esempio:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> Se è presente un errore in un'espressione regolare, come un carattere senza codice di escape e parentesi non corrispondenti, l'analisi di code coverage non funzionerà.

### <a name="other-ways-to-include-or-exclude-elements"></a>Altri modi per includere o escludere elementi

Per gli esempi, vedere l'[esempio alla fine di questo argomento](#sample).

- `ModulePath`: assembly specificati per percorso del file di assembly.

- `CompanyName`: assembly corrispondenti per attributo della società.

- `PublicKeyToken`: assembly firmati corrispondenti per token di chiave pubblica. Ad esempio per soddisfare tutti i componenti e le estensioni di Visual Studio, usare `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>`.

- `Source`: elementi corrispondenti per nome del percorso del file di origine in cui sono definiti.

- `Attribute`: elementi corrispondenti ai quali è connesso un particolare attributo. Specificare il nome completo dell'attributo, includendo "Attribute" alla fine del nome.

- `Function`: procedure, funzioni o metodi corrispondenti per nome completo.

**Corrispondenza di un nome di funzione**

L'espressione regolare deve corrispondere al nome completo della funzione, incluso lo spazio dei nomi, il nome della classe, il nome del metodo e l'elenco parametri. Ad esempio,

- C# o Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`

- C++: `Fabrikam::Math::LocalMath::SquareRoot(double)`

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

## <a name="how-to-specify-run-settings-files-while-running-tests"></a>Come specificare i file di impostazioni esecuzione test durante l'esecuzione dei test

### <a name="to-customize-run-settings-in-visual-studio-tests"></a>Per personalizzare le impostazioni esecuzione test nei test di Visual Studio

Scegliere **Test** > **Impostazioni test** > **Seleziona file di impostazioni test** e selezionare il file con estensione *runsettings*. Il file viene visualizzato nel menu Impostazioni test ed è possibile selezionarlo o annullare l'operazione. Se selezionato, il file di impostazioni esecuzione test viene applicato ogni volta che si usa **Analizza code coverage**.

### <a name="to-customize-run-settings-in-a-command-line-test"></a>Per personalizzare le impostazioni esecuzione test in un test dalla riga di comando

Per eseguire un test dalla riga di comando, usare *vstest.console.exe*. Il file di impostazioni è un parametro di questa utilità.

1. Avviare il prompt dei comandi di Visual Studio Developer:

    Nel menu **Start** di Windows scegliere **Visual Studio 2017** > **Prompt dei comandi per gli sviluppatori per VS 2017**.

2. Eseguire il comando seguente:

    `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`

### <a name="to-customize-run-settings-in-a-build-definition"></a>Per personalizzare le impostazioni esecuzione test in una definizione di compilazione

È possibile ottenere dati di code coverage da Team Build.

![Specifica delle impostazioni di esecuzione in una definizione di compilazione](../test/media/codecoverage-buildrunsettings.png)

1. Assicurarsi che il file di impostazioni esecuzione test sia selezionato.

2. In Team Explorer aprire **Compilazioni** e aggiungere o modificare una definizione di compilazione.

3. Nella pagina **Processo** espandere **Test automatizzati** > **Origine test** > **Impostazioni esecuzione test**. Selezionare il file con estensione *runsettings*.

   > [!TIP]
   > Se viene visualizzato **Assembly di test** anziché **Origine test** ed è possibile selezionare solo file con estensione *testsettings*, impostare la proprietà **Test Runner** come indicato di seguito. In **Test automatizzati** selezionare **Assembly di test** e scegliere **[...]** alla fine della riga. Nella finestra di dialogo **Aggiungi/Modifica esecuzione dei test**, impostare **Test Runner** su **Visual Studio Test Runner**.

I risultati vengono visualizzati nella sezione di riepilogo del report di compilazione.

##  <a name="sample"></a> File con estensione runsettings di esempio

Copiare questo codice e modificarlo secondo le proprie esigenze.

Per altri usi del file di impostazioni esecuzione test, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See http://msdn.microsoft.com/library/2k3te2cs.aspx.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Vedere anche

- [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)