---
title: 'Procedura: Creare un adattatore dati di diagnostica in Visual Studio | Microsoft Docs'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 22867cab68497afd54c2ffee30bb9ccc73e90862
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Procedura: creare un adattatore dati di diagnostica

Per creare un *adattatore dati di diagnostica*, è necessario creare una libreria di classi mediante Visual Studio, quindi aggiungere le API dell'adattatore dati di diagnostica fornite da Visual Studio Enterprise alla libreria di classi. Inviare tutte le informazioni desiderate come flusso o come file a <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> fornito dal framework, durante la gestione degli eventi che vengono generati durante l'esecuzione dei test. I flussi o i file inviati a <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> vengono archiviati come allegati nei risultati del test al termine di quest'ultimo. Se si crea un bug da questi risultati o quando si usa [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], anche i file vengono collegati al bug.

 È possibile creare un adattatore dati di diagnostica che influisca sul computer in cui vengono eseguiti i test oppure su un computer che fa parte dell'ambiente in uso per eseguire l'applicazione sottoposta a test, ad esempio la raccolta di file nel computer in cui vengono eseguiti i test o la raccolta di file nel computer a cui è assegnato il ruolo di server Web per l'applicazione.

 È possibile assegnare all'adattatore dati di diagnostica un nome descrittivo che viene visualizzato durante la creazione delle impostazioni test mediante Microsoft Test Manager o usando Visual Studio. Le impostazioni di test consentono di definire con quale ruolo computer verranno eseguiti adattatori dati di diagnostica specifici nell'ambiente durante l'esecuzione dei test. È inoltre possibile configurare gli adattatori dati di diagnostica quando si creano le impostazioni di test. È ad esempio possibile creare un adattatore dati di diagnostica che raccolta log personalizzati dal server Web. Quando si creano le impostazioni di test, è possibile scegliere di eseguire questo adattatore dati di diagnostica nel computer o nei computer in cui viene eseguito questo ruolo del server Web ed è possibile modificare la configurazione per le impostazioni di test per raccogliere solo gli ultimi tre log creati. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

 Eventi vengono generati quando si eseguono i test in modo che l'adattatore dati di diagnostica sia in grado di eseguire attività nel punto specifico del test.

> [!IMPORTANT]
> Questi eventi possono essere generati su thread differenti, specialmente quando si dispone di test in esecuzione in più computer. Pertanto, è necessario tenere presente i possibili problemi relativi al threading e non danneggiare inavvertitamente i dati interni dell'adattatore personalizzato. Verificare che l'adattatore dati di diagnostica sia thread-safe.

 Di seguito è riportato un elenco parziale di eventi chiave che è possibile utilizzare quando si crea l'adattatore dati di diagnostica. Per un elenco completo di eventi dell'adattatore dati di diagnostica, vedere la classe astratta <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>.

|event|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Inizio dell'esecuzione di test|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Fine dell'esecuzione di test|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Inizio di ciascun test nell'esecuzione di test|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Fine di ciascun test nell'esecuzione di test|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Inizio di ciascun passo di un test|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Fine di ciascun passo di un test|

> [!NOTE]
> Quando viene completato un test manuale, non vengono inviati altri eventi di raccolta dati all'adattatore dati di diagnostica. Quando un test viene rieseguito, gli viene assegnato un nuovo identificatore di test case. Se un utente reimposta un test durante un test, generando l'evento <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset>, oppure modifica il risultato di un passo del test, non viene inviato alcun evento di raccolta dei dati all'adattatore dati di diagnostica, ma l'identificatore del test case rimane lo stesso. Per determinare se un test case è stato reimpostato, è necessario tenere traccia dell'identificatore di test case nell'adattatore dati di diagnostica.

 Utilizzare la procedura seguente per creare un adattatore dati di diagnostica che consenta di raccogliere un file di dati basato sulle informazioni configurate alla creazione delle impostazioni di test.

 Per un progetto di adattatore dati di diagnostica di esempio completo, incluso un editor di configurazione personalizzato, vedere [Esempio di progetto per creare un adattatore dati di diagnostica](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

##  <a name="CreateAdapter"></a> Creazione e installazione di un adattatore dati di diagnostica

#### <a name="to-create-and-install-a-diagnostic-data-adapter"></a>Per creare e installare un adattatore dati di diagnostica

1.  Creare una nuova libreria di classi.

    1.  Scegliere **Nuovo** dal menu **File**, quindi selezionare **Nuovo progetto**.

    2.  Da **Tipi progetto**, selezionare il linguaggio da usare.

    3.  Da **Modelli Visual Studio installati**, selezionare **Libreria di classi**.

    4.  Digitare un nome per l'adattatore dati di diagnostica.

    5.  Scegliere **OK**.

2.  Aggiungere l'assembly **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Riferimenti**, quindi scegliere il comando **Aggiungi riferimento**.

    2.  Scegliere **.NET** e individuare **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

    3.  Scegliere **OK**.

3.  Aggiungere l'assembly **Microsoft.VisualStudio.QualityTools.Common**.

    1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Riferimenti** e scegliere **Aggiungi riferimento**.

    2.  Scegliere **/.NET** e individuare **Microsoft.VisualStudio.QualityTools.Common.dll**.

    3.  Scegliere **OK**.

4.  Aggiungere le seguenti istruzioni `using` al file della classe:

    ```csharp
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    using System.Linq;
    using System.Text;
    using System.Xml;
    using System;
    ```

5.  Aggiungere <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> alla classe dell'adattatore dati di diagnostica in modo che venga identificato come adattatore dati di diagnostica, sostituendo **Company**, **Product** e **Version** con le informazioni appropriate per l'adattatore dati di diagnostica:

    ```
    [DataCollectorTypeUri("datacollector://Company/Product/Version")]
    ```

6.  Aggiungere l'attributo <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> alla classe, sostituendo i parametri con le informazioni appropriate per l'adattatore dati di diagnostica:

    ```
    [DataCollectorFriendlyName("Collect Log Files", false)]
    ```

     Questo nome descrittivo viene visualizzato nell'attività delle impostazioni di test.

    > [!NOTE]
    > È possibile aggiungere anche <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> per specificare l'oggetto `Type` dell'editor di configurazione personalizzato per questo adattatore dati e specificare facoltativamente il file della Guida da utilizzare per l'editor.
    >
    > È inoltre possibile applicare <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> per specificare che deve essere sempre abilitato.

7.  La classe dell'adattatore dati di diagnostica deve ereditare dalla classe <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> come indicato di seguito:

    ```csharp
    public class MyDiagnosticDataAdapter : DataCollector
    ```

8.  Aggiungere le variabili locali come segue:

    ```csharp
    private DataCollectionEvents dataEvents;
    private DataCollectionLogger dataLogger;
    private DataCollectionSink dataSink;
    private XmlElement configurationSettings;
    ```

9. Aggiungere il metodo <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> e un metodo **Dispose**. Nel metodo `Initialize` è possibile inizializzare il sink dati e i dati di configurazione delle impostazioni di test, nonché registrare i gestori degli eventi che si desidera utilizzare, come indicato di seguito:

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Utilizzare il codice del gestore eventi seguente e il metodo Private per raccogliere il file di log generato durante il test:

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     Questi file sono allegati ai risultati del test. Se si crea un bug da questi risultati o quando si utilizza [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], i file vengono allegati anche al bug.

     Per usare il proprio editor per raccogliere i dati da usare nelle impostazioni test, vedere [Procedura: Creare un editor personalizzato di dati per l'adattatore dati di diagnostica](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

11. Per raccogliere un file di log quando un test viene completato in base alla configurazione effettuata dall'utente nelle impostazioni di test, è necessario creare un file `App.config` e aggiungerlo alla soluzione. Questo file ha il formato seguente e deve contenere l'URI affinché l'adattatore dati di diagnostica lo identifichi. Sostituire i valori reali a "Company/ProductName/Version".

    > [!NOTE]
    > Se non è necessario configurare informazioni per l'adattatore dati di diagnostica, non è necessario creare un file di configurazione.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > L'elemento di configurazione predefinito può contenere qualsiasi dato necessario. Se l'utente non configura l'adattatore dati di diagnostica nelle impostazioni di test, a questo verranno passati i dati predefiniti al momento dell'esecuzione. Poiché il codice XML che si aggiunge alla sezione `<DefaultConfigurations>` non fa probabilmente parte dello schema dichiarato, è possibile ignorare gli eventuali errori XML generati.
    >
    > Sono disponibili altri esempi di file di configurazione nel percorso seguente in base alla directory di installazione: **Programmi\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors**.

     Per altre informazioni sulla configurazione delle impostazioni test per usare un ambiente quando si eseguono i test, vedere [Raccogliere dati di diagnostica nei test manuali (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

     Per altre informazioni sull'installazione del file di configurazione, vedere [Procedura: Installare un adattatore dati di diagnostica personalizzato](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

12. Compilare la soluzione per creare l'assembly dell'adattatore dati di diagnostica.

13. Per informazioni sull'installazione dell'editor personalizzato, vedere [Procedura: Installare un adattatore dati di diagnostica personalizzato](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

14. Per altre informazioni sulla configurazione delle impostazioni test per usare un ambiente quando si eseguono i test, vedere [Raccogliere dati di diagnostica nei test manuali (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

15. Per selezionare l'adattatore dati di diagnostica, è necessario in primo luogo selezionare le impostazioni test esistenti o crearne di nuove in Microsoft Test Manager o in Visual Studio. L'adattatore viene visualizzato nella scheda **Dati e diagnostica** delle impostazioni test con il nome descrittivo assegnato alla classe.

16. Impostare le impostazioni test come attive. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

17. Eseguire i test utilizzando le impostazioni di test con l'adattatore dati di diagnostica selezionato.

   Il file di dati specificato verrà allegato ai risultati del test.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Raccogliere dati di diagnostica tramite impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)
- [Raccogliere dati di diagnostica nei test manuali (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)
- [Raccogliere dati di diagnostica durante i test (VSTS)](/vsts/manual-test/collect-diagnostic-data)
- [Procedura: Creare un editor personalizzato di dati per l'adattatore dati di diagnostica](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)