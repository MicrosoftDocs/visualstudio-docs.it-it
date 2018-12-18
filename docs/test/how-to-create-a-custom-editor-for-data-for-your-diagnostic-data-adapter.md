---
title: Creare un editor dati personalizzato per un adattatore dati di diagnostica in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 58c0a4e764edd27e2059175e170a9e542c285a89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Procedura: creare un editor personalizzato di dati per l'adattatore dati di diagnostica in uso

Quando si crea un adattatore dati di diagnostica, potrebbe essere necessario consentire all'utente finale di configurare dati specifici quando l'adattatore dati di diagnostica personalizzato è selezionato per le impostazioni test. È possibile, ad esempio, selezionare i dati di configurazione che specificano le chiavi del Registro di sistema da estrarre, il livello di carico di rete da simulare o la directory in cui trovare file temporanei o file di lavoro da allegare.

È necessario utilizzare un file di configurazione per configurare i valori iniziali per l'adattatore dati di diagnostica. È possibile fornire un editor personalizzato per consentire all'utente di modificare i dati di configurazione.

Per creare un editor personalizzato, è necessario creare un controllo utente che implementa <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>.

L'adattatore dati di diagnostica può utilizzare un oggetto <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> per specificare la classe dell'editor da utilizzare per la modifica delle impostazioni di configurazione dei dati di diagnostica.

Specificare inoltre i dati di configurazione predefiniti che si desidera utilizzare.  Per una configurazione predefinita di esempio, vedere [Esempio di progetto per creare un adattatore dati di diagnostica](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

Utilizzare la procedura seguente per creare un editor personalizzato per aggiornare i dati per le impostazioni di test quando si utilizza l'adattatore dati di diagnostica personalizzato.

> [!NOTE]
> Per creare un editor personalizzato, è innanzitutto necessario creare l'adattatore dati di diagnostica con l'oggetto <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> applicato alla classe. È possibile utilizzare la proprietà <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> facoltativa in tale attributo per specificare l'origine del contenuto della Guida per l'editor. Per altre informazioni su come creare l'adattatore dati di diagnostica, vedere [Procedura: Creare un adattatore dati di diagnostica](../test/how-to-create-a-diagnostic-data-adapter.md).

Per un progetto di adattatore dati di diagnostica di esempio completo, incluso un editor di configurazione personalizzato, vedere [Esempio di progetto per creare un adattatore dati di diagnostica](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>Per creare un editor personalizzato per l'adattatore dati di diagnostica

1.  Creare un controllo utente nel progetto per l'adattatore dati di diagnostica:

    1.  Fare clic con il pulsante destro del mouse sul progetto codice che contiene la classe dell'adattatore dati di diagnostica, scegliere **Aggiungi**, quindi **Controllo utente**.

    2.  Per questo esempio, aggiungere un'etichetta al form con il testo **Data File Name:** e una casella di testo denominata **FileTextBox**, per consentire all'utente di immettere i dati necessari.

    > [!NOTE]
    > Sono attualmente supportati solo i controlli utente Windows Form.

2.  Aggiungere queste righe alla sezione della dichiarazione:

    ```csharp
    using System.Xml;
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    ```

3.  Creare il controllo utente in un editor personalizzato.

    1.  Fare clic con il pulsante destro del mouse sul controllo utente nel progetto codice, quindi scegliere **Visualizza codice**.

    2.  Impostare la classe per implementare l'interfaccia dell'editor <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> come indicato di seguito:

    ```csharp
    public partial class MyDataConfigEditor :
         UserControl, IDataCollectorConfigurationEditor
    ```

    1.  Fare clic con il pulsante destro del mouse su <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> nel codice e scegliere il comando **Implementa interfaccia**. I metodi che è necessario implementare per l'interfaccia verranno aggiunti alla classe.

    2.  Aggiungere <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> al controllo utente per l'editor in modo che venga identificato come editor dell'adattatore dati di diagnostica, sostituendo **Società**, **Prodotto** e **Versione** con le informazioni appropriate per l'adattatore dati di diagnostica:

        ```csharp
        [DataCollectorConfigurationEditorTypeUri(
            "configurationeditor://MyCompany/MyConfigEditor/1.0")]
        ```

4.  Aggiungere due variabili private come segue:

    ```csharp
    private DataCollectorSettings collectorSettings;
    private IServiceProvider ServiceProvider { get; set; }
    ```

5.  Aggiungere il codice per inizializzare l'editor per l'adattatore dati di diagnostica. È possibile aggiungere valori predefiniti ai campi nel controllo utente utilizzando dati nella variabile delle impostazioni. Si tratta dei dati presenti nell'elemento `<DefaultConfiguration>` del file di configurazione XML per l'adattatore.

    ```csharp
    public void Initialize(
        IServiceProvider svcProvider,
        DataCollectorSettings settings)
    {
        ServiceProvider = svcProvider;
        collectorSettings = settings;

        // Display the default file name as listed in the settings file.
        this.SuspendLayout();
        this.FileTextBox.Text = getText(collectorSettings.Configuration);
        this.ResumeLayout();
    }
    ```

6.  Aggiungere il codice per salvare nuovamente i dati dai controlli nell'editor nel formato XML richiesto dall'API dell'adattatore dati di diagnostica, come indicato di seguito:

    ```csharp
    public DataCollectorSettings SaveData()
    {
        collectorSettings.Configuration.InnerXml =
            String.Format(
    @"<MyCollectorName
        xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
      <File FullPath=""{0}"" />
    </MyCollectorName>",
        FileTextBox.Text);
        return collectorSettings;
    }
    ```

7.  Se lo si desidera, aggiungere il codice per verificare che i dati siano corretti nel metodo `VerifyData`. In alternativa, è possibile fare in modo che il metodo restituisca `true`.

    ```csharp
    public bool VerifyData()
    {
        // Not currently verifying data
        return true;
    }
    ```

8.  (Facoltativo) È possibile aggiungere codice per ripristinare in base alle impostazioni iniziali i dati forniti nel file di configurazione XML nel metodo `ResetToAgentDefaults()`, che utilizza il metodo privato `getText()`.

    ```csharp
    // Reset to default value from XML configuration
    // using a custom getText() method
    public void ResetToAgentDefaults()
    {
        this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
    }

    // Local method to read the configuration settings
    private string getText(XmlElement element)
    {
        // Setup namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                element.OwnerDocument.NameTable);

        // Find all the "File" elements under our configuration
        XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

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
    ```

9. Compilare la soluzione. Copiare l'assembly dell'adattatore dati di diagnostica e il file di configurazione XML (`<diagnostic data adapter name>.dll.config`) nel percorso seguente, in base alla directory di installazione: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Sebbene l'editor di configurazione possa trovarsi in un progetto e in un assembly diversi dall'adattatore dati di diagnostica, è anche possibile che si trovino nello stesso assembly.

10. Per usare l'adattatore dati di diagnostica nei test, è necessario selezionarlo dall'elenco delle impostazioni test esistenti oppure crearne uno nuovo da Microsoft Test Manager o da Visual Studio, quindi selezionarlo.

     L'adattatore viene visualizzato nella scheda **Dati e diagnostica** delle impostazioni test con il nome descrittivo assegnato alla classe.

11. Per configurare l'adattatore dati di diagnostica per le impostazioni test, scegliere **Configura** accanto al nome dell'adattatore.

     Verrà visualizzato l'editor personalizzato.

12. Modificare i campi nell'editor personalizzato in base alle esigenze, quindi scegliere **Salva**.

13. Se i test vengono eseguiti da Microsoft Test Manager, è possibile assegnare queste impostazioni test al piano di test prima di eseguire i test oppure usare il comando **Esegui con opzioni** per assegnare impostazioni test ed eseguire l'override delle impostazioni test. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

14. Per poter utilizzare il nuovo editor di configurazione con un adattatore dati di diagnostica, è necessario applicare <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> a ogni classe dell'adattatore dati di diagnostica con cui si desidera utilizzare l'editor, quindi ricompilarli e reinstallarli nel computer client. Per altre informazioni sull'installazione di adattatori dati di diagnostica e di editor di configurazione, vedere [Procedura: Installare un adattatore dati di diagnostica personalizzato](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Eseguire i test utilizzando le impostazioni di test con l'adattatore dati di diagnostica selezionato.

     Il file di dati specificato nell'editor verrà allegato ai risultati del test.

 Per altre informazioni sulla configurazione delle impostazioni test per usare un ambiente quando si eseguono i test, vedere [Raccogliere dati diagnostici durante i test (VSTS)](/vsts/manual-test/collect-diagnostic-data) o [Raccogliere dati diagnostici nei test manuali (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Creazione di un adattatore dati di diagnostica per raccogliere dati personalizzati o per influire su un computer di test](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Raccogliere dati di diagnostica tramite impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)
- [Esempio di progetto per creare un adattatore dati di diagnostica](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)