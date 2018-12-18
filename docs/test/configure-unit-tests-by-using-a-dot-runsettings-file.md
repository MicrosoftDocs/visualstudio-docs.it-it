---
title: Configurare unit test in Visual Studio usando un file con estensione runsettings | Microsoft Docs
ms.date: 02/28/2018
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3a446c3223197058401e07a5aef2cb13bde46f3c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurare unit test usando un file con estensione *runsettings*

Gli unit test in Visual Studio possono essere configurati usando un file con estensione *runsettings*. Ad esempio, è possibile modificare la versione di .NET Framework in cui vengono eseguiti i test, la directory dei risultati di test e i dati raccolti durante l'esecuzione dei test.

> [!NOTE]
> Il nome del file non è rilevante, purché si usi l'estensione "runsettings".

Se non è richiesta una configurazione particolare, non sarà necessario alcun file con estensione *runsettings*. L'uso più comune di un file con estensione *runsettings* è la personalizzazione dell'[analisi code coverage](../test/customizing-code-coverage-analysis.md).

## <a name="customize-tests"></a>Personalizzare i test

1. Aggiungere un file XML alla soluzione di Visual Studio e rinominarlo in *test.runsettings*.

1. Sostituire il contenuto del file con il codice XML dell'esempio riportato di seguito e personalizzarlo in base alle esigenze.

1. Nel menu **Test** scegliere **Impostazioni test** > **Seleziona file di impostazioni test**.

È possibile creare più file con estensione *runsettings* nella soluzione e abilitarli o disabilitarli in momenti diversi tramite il menu **Impostazioni test**.

![Abilitazione di un file di impostazioni di esecuzione](../test/media/runsettings-1.png)

## <a name="example-runsettings-file"></a>Esempio di file con estensione *runsettings*

Di seguito è riportato un tipico file con estensione *runsettings*. Ogni elemento del file è facoltativo, perché ogni valore ha un'impostazione predefinita.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

     <!--TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
     <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
     <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

Il file con estensione *runsettings* viene usato anche per configurare l'[analisi code coverage](../test/customizing-code-coverage-analysis.md).

Nella parte restante di questo argomento viene descritto il contenuto del file.

## <a name="edit-your-runsettings-file"></a>Modificare il file con estensione *runsettings*

Le sezioni che seguono descrivono in dettaglio gli elementi di un file con estensione *runsettings*.

### <a name="test-run-configuration"></a>Configurazione dell'esecuzione dei test

|Nodo|Impostazione predefinita|Valori|
|----------|-------------|------------|
|`ResultsDirectory`||Directory in cui vengono inseriti i risultati del test.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Questa impostazione indica quale versione del framework unit test viene usata per trovare ed eseguire i test. Può essere diversa dalla versione della piattaforma .NET specificata nelle proprietà di compilazione del progetto di unit test.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|False|false, true|
|`TestAdaptersPaths`||Uno o più percorsi della directory in cui si trovano i TestAdapter.|
|`MaxCpuCount`|1|Questa impostazione determina il livello di esecuzione parallela dei test durante l'esecuzione di unit test, in base ai core disponibili nel computer. Il motore di esecuzione dei test viene avviato come processo distinto in ogni core disponibile e assegna a ogni core un contenitore con test da eseguire. Un contenitore può essere un assembly, una DLL o un artefatto pertinente. Il contenitore di test è l'unità di pianificazione. In ogni contenitore, i test vengono eseguiti in base al framework di test. Se sono presenti molti contenitori di questo tipo, non appena termina l'esecuzione dei test in un contenitore, i processi vengono assegnati al successivo contenitore disponibile.<br /><br /> MaxCpuCount può essere:<br /><br /> n, dove 1 < = n < = numero di core: verranno avviati fino a n processi<br /><br /> n, dove n = qualsiasi altro valore: il numero massimo di processi avviati corrisponderà ai core disponibili nel computer|
|`TestSessionTimeout`||Consente agli utenti di terminare una sessione di test allo scadere di un timeout specificato. L'impostazione di un timeout assicura un consumo ottimale delle risorse e consente di vincolare le sessioni di test a un periodo di tempo stabilito. L'impostazione è disponibile in **Visual Studio 2017 versione 15.5** e versioni successive.

### <a name="diagnostic-data-adapters-data-collectors"></a>Adattatori dati di diagnostica (agenti di raccolta dati)

L'elemento `DataCollectors` specifica le impostazioni degli adattatori dati di diagnostica. Gli adattatori dati di diagnostica raccolgono informazioni aggiuntive sull'ambiente e l'applicazione sottoposta a test. Le impostazioni di ogni adattatore sono predefinite. È quindi necessario specificarle solo se non si vogliono usare quelle predefinite.

#### <a name="code-coverage-adapter"></a>Adattatore di code coverage

L'agente di raccolta dati di code coverage crea un log in cui le parti del codice dell'applicazione sono state eseguite nel test. Per altre informazioni sulla personalizzazione delle impostazioni per il code coverage, vedere [Customizing Code Coverage Analysis](../test/customizing-code-coverage-analysis.md) (Personalizzazione dell'analisi del code coverage).

#### <a name="video-data-collector"></a>Agente di raccolta dati video

L'agente di raccolta dati video acquisisce la registrazione di una schermata quando si eseguono i test. La registrazione è utile per la risoluzione dei test dell'interfaccia utente. L'agente di raccolta dati video è disponibile in **Visual Studio 2017 versione 15.5** e versioni successive.

Per personalizzare qualsiasi altro tipo di adattatore dati di diagnostica, è necessario usare un [file di impostazioni di test](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

TestRunParameters consente di definire le variabili e i valori disponibili per i test in fase di esecuzione. Queste variabili sono accessibili tramite l'oggetto [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx).

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
```

Per usare TestContext, aggiungere un campo [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx) privato e una proprietà `TestContext` pubblica alla classe di test.

### <a name="mstest-run-settings"></a>Impostazioni di esecuzione MSTest

Queste impostazioni sono specifiche dell'adattatore di test che esegue i metodi di test con l'attributo `[TestMethod]` .

|Configurazione|Impostazione predefinita|Valori|
|-------------------|-------------|------------|
|ForcedLegacyMode|False|In Visual Studio 2012, l'adapter MSTest è stato ottimizzato per essere più veloce e più scalabile. Un comportamento, ad esempio l'ordine in cui vengono eseguiti i test, potrebbe non essere esattamente come quello nelle versioni precedenti di Visual Studio. Impostare questo valore su `true` per usare l'adattatore di test precedente.<br /><br /> Lo si può usare, ad esempio, nel caso in cui sia presente un file *app.config* specificato per uno unit test.<br /><br /> È consigliabile provare a effettuare il refactoring dei test per consentire l'uso dell'adattatore più recente.|
|IgnoreTestImpact|False|La funzionalità dell'impatto sui test assegna la priorità ai test interessati da modifiche recenti, una volta eseguiti in MSTest o da Microsoft Test Manager. Questa impostazione disattiva la funzionalità. Per altre informazioni, vedere [Procedura: Raccogliere dati per verificare i test da eseguire dopo che sono state apportate modifiche al codice](http://msdn.microsoft.com/Library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||È possibile specificare un file di impostazioni di test da usare con l'adattatore MSTest. È inoltre possibile specificare un file di impostazioni test usando il menu **Test**, **Impostazioni test**, **Seleziona file di impostazioni test**.<br /><br /> Se si specifica questo valore, è necessario impostare anche **ForcedlegacyMode** su **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|False|Una volta completata l'esecuzione di un test, MSTest viene arrestato. Anche qualsiasi processo avviato come parte del test verrà interrotto. Se si desidera che l'executor di test rimanga attivo, impostare questa configurazione su true.<br /><br /> Lo si può usare, ad esempio, per mantenere in esecuzione il browser tra i test codificati dell'interfaccia utente.|
|DeploymentEnabled|true|Se si imposta il valore su false, gli elementi della distribuzione specificati nel metodo di test non verranno copiati nella directory di distribuzione.|
|CaptureTraceOutput|true|È possibile scrivere nella traccia di debug dal metodo di test usando Trace.WriteLine. Usando questa configurazione, è possibile disattivare queste tracce di debug.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|È possibile mantenere la directory di distribuzione dopo un'esecuzione di test impostando questo valore su false.|
|MapInconclusiveToFailed|False|Se lo stato di un test è Senza risultati, in genere ne viene eseguito il mapping allo stato Ignorato in Esplora test. Se si vuole che i test senza risultati vengano visualizzati come Senza risultati, usare questa configurazione.|
|InProcMode|False|Se si desidera che i test vengano eseguiti nello stesso processo dell'adattatore MSTest, impostare questo valore su true. Questa impostazione fornisce un lieve miglioramento delle prestazioni. Se un test viene terminato con un'eccezione, gli altri test non proseguono.|
|AssemblyResolution|False|È possibile specificare i percorsi di assembly aggiuntivi durante la ricerca e l'esecuzione di unit test. Ad esempio, è possibile usare questi percorsi per gli assembly di dipendenza che non si trovano nella stessa directory dell'assembly di test. Per specificare un percorso, usare un elemento "Directory Path". I percorsi possono contenere variabili di ambiente.<br /><br /> `<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Vedere anche

- [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md)