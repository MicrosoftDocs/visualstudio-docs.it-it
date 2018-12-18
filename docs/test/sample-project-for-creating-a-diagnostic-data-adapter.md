---
title: Progetto di esempio per la creazione di un adattatore dati di diagnostica in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 98606c5afbeed035392f35d71de60bb4d4bbb5a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>Esempio di progetto per creare un adattatore dati di diagnostica

"MyDiagnosticDataAdapter" è un adattatore dati di diagnostica semplice in grado di allegare un file di log ai risultati dei test quando si eseguono i test.

 Sono necessarie autorizzazioni amministrative nel computer in cui viene installato l'editor di configurazione o l'agente di raccolta dati di diagnostica.

## <a name="example-data-adapter"></a>Adattatore dati di esempio

In questo esempio viene illustrato come eseguire le attività seguenti:

-   Applicare attributi per rendere individuabile una classe per Microsoft Test Manager come adattatore dati di diagnostica.

-   Applicare attributi per rendere individuabile una classe di controllo utente per Microsoft Test Manager come editor da usare per modificare la configurazione per un adattatore dati di diagnostica.

-   Accedere ai dati di configurazione predefiniti.

-   Eseguire la registrazione di eventi di raccolta dati diagnostici specifici.

-   Allegare il file di log inviandolo a <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>.

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
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
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
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

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
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
    }
}
```

## <a name="example-configuration-editor"></a>Esempio di editor di configurazione

Si tratta di un editor di configurazione di esempio per l'adattatore dati di diagnostica. Aggiungere un controllo utente al progetto e creare un form molto semplice con un'etichetta ("Nome file di log:") e una casella di testo denominata "FileTextBox".

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

            string result = String.Empty;
            if (files.Count > 0)
            {
                XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result = pathAttribute.Value;
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-file"></a>Esempio di file di configurazione

Di seguito è riportato un file di configurazione di esempio per l'editor di configurazione dell'agente di raccolta dati diagnostici.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compiling-the-code"></a>Compilazione del codice

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>Per creare il progetto di codice per questo adattatore diagnostico

1.  Creare un nuovo progetto libreria di classi denominato "MyDataCollector".

2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Proprietà**. Per selezionare una cartella da aggiungere, scegliere **Percorsi riferimento**, quindi scegliere i puntini di sospensione (**...**).

     Viene visualizzata la finestra di dialogo **Seleziona percorso riferimenti**.

3.  Selezionare il percorso seguente, basato sulla directory di installazione: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*. Scegliere **OK**.

4.  Per aggiungere la cartella al percorso di riferimento, scegliere **Aggiungi cartella**.

     La cartella verrà visualizzata nell'elenco di percorsi di riferimento.

5.  Scegliere l'icona **Salva tutto** per salvare i percorsi di riferimento.

6.  Aggiungere l'assembly **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Riferimenti** e quindi scegliere **Aggiungi riferimento**.

    2.  Scegliere **Sfoglia** e individuare **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

         Questo assembly è reperibile in *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Scegliere **OK**.

7.  Aggiungere l'assembly **Microsoft.VisualStudio.QualityTools.Common**.

    1.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Riferimenti** e selezionare **Aggiungi riferimento**.

    2.  Scegliere **Sfoglia** e individuare **Microsoft.VisualStudio.QualityTools.Common.dll**.

         Questo assembly è reperibile in *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Scegliere **OK**.

8.  Copiare la classe dell'adattatore dati di diagnostica elencata in precedenza in questo documento nella classe per la libreria di classi. Salvare questa classe.

9. Per aggiungere un controllo utente al progetto, fare clic con il pulsante destro del mouse sul progetto MyDataCollector in Esplora soluzioni, scegliere **Aggiungi** e quindi **Controllo utente**. Scegliere **Aggiungi**.

10. Usando la casella degli strumenti, aggiungere un'etichetta al controllo utente e modificare la proprietà Text in **Nome file:**.

11. Usando la casella degli strumenti, aggiungere una casella di testo al controllo utente e modificare il nome in **textBoxFileName**.

12. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul controllo utente, quindi scegliere **Visualizza codice.** Sostituire questa classe del controllo utente con la classe del controllo utente elencata in precedenza in questo documento. Salvare questa classe.

    > [!NOTE]
    > Per impostazione predefinita, il controllo utente viene denominato UserControl1. Assicurarsi che nel codice della classe del controllo utente sia utilizzato il nome del controllo utente.

13. Per creare il file di configurazione, in **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi** e quindi scegliere **Nuovo elemento**. Fare clic per selezionare **File di configurazione dell'applicazione**, quindi scegliere **Aggiungi**. Alla soluzione verrà aggiunto un file denominato **App.config**.

14. Copiare il codice XML dell'esempio precedente nel file XML. Salvare il file.

15. Compilare la soluzione, quindi copiare l'assembly compilato e il file `App.config` nella directory *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

16. Creare le impostazioni di test che utilizzano questo adattatore diagnostico di dati personalizzati. Configurare le impostazioni di test per raccogliere un file esistente.

     Se i test vengono eseguiti da Microsoft Test Manager, è possibile assegnare queste impostazioni di test al piano di test prima di eseguire i test oppure usare il comando Esegui con opzioni per assegnare impostazioni di test ed eseguire l'override delle impostazioni di test. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

17. Eseguire i test utilizzando le impostazioni di test con l'adattatore dati di diagnostica selezionato.

     Il file di dati specificato verrà allegato ai risultati del test quando questo viene eseguito.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare un adattatore dati di diagnostica](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Procedura: Creare un editor personalizzato di dati per l'adattatore dati di diagnostica](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Procedura: Installare un adattatore dati di diagnostica personalizzato](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [Creazione di un adattatore dati di diagnostica per raccogliere dati personalizzati o per influire su un computer di test](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)