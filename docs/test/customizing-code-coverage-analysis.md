---
title: Personalizzazione dell'analisi code coverage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: e0a27e78735b85417a62d99e4f9b5d101a7a177d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="customizing-code-coverage-analysis"></a>Personalizzazione dell'analisi code coverage

Per impostazione predefinita, lo strumento per il code coverage di Visual Studio analizza tutti gli assembly della soluzione (.exe/.dll) caricati durante gli unit test. È consigliabile mantenere questa impostazione predefinita in quanto funziona bene nella maggior parte dei casi. Per altre informazioni, vedere [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
Prima di personalizzare il comportamento del code coverage, considerare alcune alternative:  
  
-   *Si vuole escludere il codice di test dai risultati del code coverage e includere solo il codice dell'applicazione.*  
  
     Aggiungere `ExcludeFromCodeCoverage Attribute` alla classe di test.  
  
-   *Si vogliono includere assembly che non fanno parte della soluzione.*  
  
     Ottenere i file con estensione pdb per questi assembly e copiarli nella stessa cartella dei file con estensione dll dell'assembly.  
  
Per personalizzare il comportamento del code coverage, copiare l'[esempio alla fine di questo argomento](#sample) e aggiungerlo alla soluzione mediante l'estensione di file runsettings. Modificarlo secondo le proprie esigenze e quindi nel menu **Test** scegliere **Impostazioni test** e **Seleziona file di impostazioni test**. Nella parte restante di questo argomento questa procedura viene descritta più dettagliatamente.  
  
## <a name="the-runsettings-file"></a>File con estensione runsettings

Le impostazioni avanzate di code coverage vengono specificate in un file con estensione runsettings. Si tratta del file di configurazione usato dagli strumenti di testing unità. Si consiglia di copiare l'[esempio alla fine di questo argomento](#sample) e di modificarlo in base alle proprie esigenze.  
  
-   *Cosa è successo nel file con estensione testsettings usato in Visual Studio 2010?*  
  
     In Visual Studio 2010 il file con estensione testsettings si applica solo agli unit test basati sul framework MSTest. In Visual Studio 2012, gli strumenti di test sono validi non solo per MSTest, ma anche altri framework come NUnit e xUnit.net. Il file con estensione testsettings non funzionerà con questi framework. Il file con estensione runsettings è progettato per personalizzare gli strumenti di test in modo da funzionare con tutti i framework di test.  
  
 Per personalizzare il code coverage, sarà necessario aggiungere un file con estensione runsettings alla soluzione:  
  
1.  Aggiungere un file XML con estensione `.runsettings` come elemento della soluzione:  
  
     In Esplora soluzioni scegliere **Aggiungi**, **Nuovo elemento** dal menu di scelta rapida della soluzione e selezionare **File XML**. Salvare il file e assegnargli un nome che termina con `CodeCoverage.runsettings`.  
  
2.  Aggiungere il contenuto fornito nell'esempio alla fine di questo argomento, quindi personalizzarlo secondo le proprie esigenze come descritto nelle sezioni seguenti.  
  
3.  Nel menu **Test** scegliere **Impostazioni test**, **Seleziona file di impostazioni test** e selezionare il file.  
  
4.  Quando si esegue **Analizza code coverage**, questo file `.runsettings` ne controllerà il comportamento. Si tenga presente che è necessario eseguire nuovamente il code coverage: i risultati del code coverage precedenti e la colorazione del codice non vengono nascosti automaticamente quando si eseguono i test o si aggiorna il codice.  
  
5.  Per attivare e disattivare le impostazioni personalizzate, deselezionare o selezionare il file nel menu **Test**, **Impostazioni test**.  
  
 ![Menu Impostazioni test con file di impostazioni personalizzato](../test/media/codecoverage-settingsfile.png "CodeCoverage-settingsFile")  
  
 Altri aspetti degli unit test possono essere configurati nello stesso file con estensione runsettings. Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).  
  
### <a name="specifying-symbol-search-paths"></a>Specifica dei percorsi di ricerca dei simboli

Il code coverage richiede che siano presenti i simboli (file con estensione pdb) per gli assembly. Per gli assembly compilati dalla soluzione, i file di simboli sono solitamente presenti accanto ai file binari e il code coverage viene eseguito automaticamente. In alcuni casi invece è consigliabile includere assembly a cui si fa riferimento nell'analisi del code coverage. In tali casi, i file con estensione pdb non possono essere adiacenti ai binari, ma è possibile specificare il percorso di ricerca dei simboli nel file con estensione runsettings.  
  
```xml  
<SymbolSearchPaths>                
      <Path>\\mybuildshare\builds\ProjectX</Path>  
      <!--More paths if required-->  
</SymbolSearchPaths>  
  
```  
  
> [!WARNING]
>  La risoluzione dei simboli può richiedere tempo, in particolare quando si usa un percorso di file remoto con molti assembly. Di conseguenza, si consiglia di copiare i file remoti con estensione pdb nello stesso percorso locale dei file binari (.dll ed .exe).  
  
### <a name="excluding-and-including"></a>Esclusione ed inclusione

È possibile escludere gli assembly specificati dall'analisi code coverage. Ad esempio:  
  
```minterastlib  
<ModulePaths>  
  <Exclude>  
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Exclude>  
</ModulePaths>  
```  
  
 In alternativa, è possibile specificare gli assembly che devono essere inclusi. Questo approccio presenta lo svantaggio che quando si aggiungono più assembly alla soluzione, è necessario tenere a mente che occorre aggiungerli anche all'elenco:  
  
```minterastlib  
<ModulePaths>  
  <Include>  
   <ModulePath>Fabrikam.Math.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Include>  
</ModulePaths>  
```  
  
 Se `<Include>` è vuoto, l'elaborazione del code coverage include tutti gli assembly (file con estensione dll ed exe) caricati e che dispongono di file con estensione **.pdb**, ad eccezione degli elementi che soddisfano una clausola di un elenco `<Exclude>`.  
  
 `Include` viene elaborato prima `Exclude`.  
  
### <a name="regular-expressions"></a>Espressioni regolari

Includere ed escludere i nodi che usano le espressioni regolari. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Le espressioni regolari non equivalgono ai caratteri jolly. In particolare:  
  
1.  **.\*** corrisponde a una stringa composta da qualsiasi carattere  
  
2.  **\\.** corrisponde a un punto "."  
  
3.  **\\(   \\)** corrisponde alle parentesi "(  )"  
  
4.  **\\\\** corrisponde al delimitatore del percorso di file "\\"  
  
5.  **^** corrisponde all'inizio della stringa  
  
6.  **$** corrisponde alla fine della stringa  
  
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
>  Se è presente un errore in un'espressione regolare, come un carattere senza codice di escape e parentesi non corrispondenti, l'analisi di code coverage non funzionerà.  
  
### <a name="other-ways-to-include-or-exclude-elements"></a>Altri modi per includere o escludere elementi  
 Per gli esempi, vedere l'[esempio alla fine di questo argomento](#sample).  
  
-   `ModulePath`: assembly specificati per percorso del file di assembly.  
  
-   `CompanyName`: assembly corrispondenti per attributo della società.  
  
-   `PublicKeyToken`: assembly firmati corrispondenti per token di chiave pubblica. Ad esempio per soddisfare tutti i componenti e le estensioni di Visual Studio, usare `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>`.  
  
-   `Source`: elementi corrispondenti per nome del percorso del file di origine in cui sono definiti.  
  
-   `Attribute`: elementi corrispondenti ai quali è connesso un particolare attributo. Specificare il nome completo dell'attributo, includendo "Attribute" alla fine del nome.  
  
-   `Function`: procedure, funzioni o metodi corrispondenti per nome completo.  
  
 **Corrispondenza di un nome di funzione**  
  
 L'espressione regolare deve corrispondere al nome completo della funzione, incluso lo spazio dei nomi, il nome della classe, il nome del metodo e l'elenco parametri. Ad esempio,  
  
-   C# o Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`  
  
-   C++: `Fabrikam::Math::LocalMath::SquareRoot(double)`  
  
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
  
## <a name="how-to-specify-runsettings-files-while-running-tests"></a>Come specificare file con estensione runsettings durante l'esecuzione dei test  
  
### <a name="to-customize-runsettings-in-visual-studio-tests"></a>Per personalizzare i file con estensione runsettings nei test di Visual Studio

Scegliere **Test** > **Impostazioni test** > **Seleziona file di impostazioni test** e selezionare il file RUNSETTINGS. Il file viene visualizzato nel menu Impostazioni test ed è possibile selezionarlo o annullare l'operazione. Quando viene selezionato, il file con estensione runsettings viene applicato ogni volta che si usa **Analizza code coverage**.

### <a name="to-customize-run-settings-in-a-command-line-test"></a>Per personalizzare le impostazioni esecuzione test in un test da riga di comando

Per eseguire un test dalla riga di comando usare vstest.console.exe. Il file di impostazioni è un parametro di questa utilità.

1.  Avviare il prompt dei comandi di Visual Studio Developer:

    Nel menu **Start** di Windows scegliere **Visual Studio 2017** > **Prompt dei comandi per gli sviluppatori per VS 2017**.

2.  Eseguire il comando seguente:

    `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`

### <a name="to-customize-run-settings-in-a-build-definition"></a>Per personalizzare le impostazioni esecuzione test in una definizione di compilazione

È possibile ottenere dati di code coverage da Team Build.

![Specifica delle impostazioni esecuzione test in una definizione di compilazione](../test/media/codecoverage-buildrunsettings.png "CodeCoverage-buildRunsettings")  

1.  Assicurarsi che il file con estensione runsettings sia selezionato.  
  
2.  In Team Explorer aprire **Compilazioni** e aggiungere o modificare una definizione di compilazione.  
  
3.  Nella pagina **Processo** espandere **Test automatizzati** > **Origine test** > **Impostazioni esecuzione test**. Selezionare il file con estensione **runsettings**.
  
    -   *Viene visualizzato **Assembly di test** anziché **Origine test**. Quando si prova ad impostare il campo **Impostazioni esecuzione test**, è possibile selezionare solo file con estensione testsettings.*  
  
         In **Test automatizzati** selezionare **Assembly di test** e scegliere **[...]** alla fine della riga. Nella finestra di dialogo **Aggiungi/Modifica esecuzione dei test**, impostare **Test Runner** su **Visual Studio Test Runner**.  
  
I risultati vengono visualizzati nella sezione di riepilogo del report di compilazione.
  
##  <a name="sample"></a> File con estensione runsettings di esempio

Copiare questo codice e modificarlo secondo le proprie esigenze. Questa è l'impostazione predefinita del file con estensione runsettings.

Per altri usi del file con estensione runsettings, vedere [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

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

[Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)  
[Eseguire unit test del codice](../test/unit-test-your-code.md)
