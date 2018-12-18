---
title: Creare un componente aggiuntivo di Visual Studio per il Visualizzatore risultati test prestazioni Web | Microsoft Docs
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: aa163381415060d189899e7defd64a8935c4ea94
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-visual-studio-add-in-for-the-web-performance-test-results-viewer"></a>Procedura: creare un componente aggiuntivo di Visual Studio per il Visualizzatore risultati test prestazioni Web

È possibile estendere l'interfaccia utente per il Visualizzatore risultati test prestazioni Web utilizzando gli spazi dei nomi seguenti:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

-   <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Inoltre, è necessario aggiungere un riferimento alla DLL LoadTestPackage disponibile nella cartella *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

-   Per estendere l'interfaccia utente del Visualizzatore risultati test prestazioni Web, è necessario creare un controllo utente e un componente aggiuntivo per Visual Studio. Nelle procedure seguenti viene illustrato come creare il componente aggiuntivo e il controllo utente nonché come implementare le classi necessarie per estendere l'interfaccia utente del Visualizzatore risultati test prestazioni Web.

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Creare o aprire una soluzione contenente un'applicazione Web ASP.NET ed un progetto di test di carico e prestazioni Web

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Per preparare l'estensione del Visualizzatore risultati test prestazioni Web

Creare o aprire una soluzione non di produzione con la quale sperimentare che contenga un'applicazione Web ASP.NET e un progetto di test di carico e prestazioni Web con uno o più test delle prestazioni Web per l'applicazione Web ASP.NET.

> [!NOTE]
> È possibile creare un'applicazione Web ASP.NET e un progetto di test prestazioni Web e di carico che contiene test prestazioni Web seguendo le procedure in [Procedura: Creare un test di servizio Web](../test/how-to-create-a-web-service-test.md) e [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Creare un componente aggiuntivo per Visual Studio

Un componente aggiuntivo è una DLL compilata che viene eseguita nell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) di Visual Studio. La compilazione garantisce la protezione della proprietà intellettuale e consente il miglioramento delle prestazioni. Sebbene sia possibile creare manualmente componenti aggiuntivi, l'utilizzo della Creazione guidata componente aggiuntivo rende l'operazione molto più semplice. La Creazione guidata componente aggiuntivo consente di generare un componente aggiuntivo di base completamente funzionale che può essere eseguito immediatamente dopo la creazione. Al termine della generazione del programma di base tramite la Creazione guidata componente aggiuntivo, sarà possibile aggiungere codice a tale programma e personalizzarlo.

 La procedura guidata del componente aggiuntivo consente di fornire un nome visualizzato e una descrizione per il componente aggiuntivo. Entrambi saranno visualizzati nella finestra di dialogo **Gestione componenti aggiuntivi**. Facoltativamente, è possibile scegliere di generare automaticamente nella procedura guidata il codice che aggiunge al menu **Strumenti** un comando per l'apertura del componente aggiuntivo. È anche possibile scegliere di visualizzare una finestra **Informazioni su** personalizzata per il componente aggiuntivo. Al termine della procedura guidata, si disporrà di un nuovo progetto con una sola classe tramite la quale viene implementato il componente aggiuntivo. Tale classe viene denominata Connect.

 Si utilizzerà **Gestione componenti aggiuntivi** alla fine di questo argomento.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Per creare un componente aggiuntivo utilizzando la Creazione guidata componente aggiuntivo.

1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi** e quindi **Nuovo progetto**.

     Verrà visualizzata la finestra di dialogo Nuovo progetto.

2.  In **Modelli installati** espandere **Altri tipi di progetto** e selezionare **Extensibility**.

3.  Nell'elenco dei modelli selezionare **Componente aggiuntivo Visual Studio**.

4.  In Nome digitare un nome per il componente aggiuntivo. Ad esempio, **WebPerfTestResultsViewerAddin**.

5.  Scegliere **OK**.

     Verrà avviata la Creazione guidata componente aggiuntivo di Visual Studio.

6.  Scegliere **Avanti**.

7.  Nella pagina **Selezionare un linguaggio di programmazione** selezionare il linguaggio di programmazione che si vuole usare per la compilazione del componente aggiuntivo.

    > [!NOTE]
    > In questo argomento viene utilizzato Visual C# per il codice di esempio.

8.  Nella pagina **Selezionare un host applicazioni** selezionare **Visual Studio**, quindi deselezionare **Visual Studio Macros**.

9. Scegliere **Avanti**.

10. Digitare il nome e la descrizione del componente aggiuntivo nella pagina **Specificare un nome e una descrizione**.

     Dopo aver creato il componente aggiuntivo, il nome e la descrizione corrispondenti verranno visualizzati nell'elenco **Componenti aggiuntivi disponibili** nella finestra di dialogo **Gestione componenti aggiuntivi**. Aggiungere alla descrizione del componente aggiuntivo delle informazioni sufficientemente dettagliate che consentano agli utenti di apprenderne il comportamento, il funzionamento e così via.

11. Scegliere **Avanti**.

12. Nella pagina **Scegliere le opzioni del componente aggiuntivo** selezionare **Carica il componente aggiuntivo all'avvio dell'applicazione host**.

13. Deselezionare le caselle di controllo rimanenti.

14. Nella pagina **Scelta della finestra 'Informazioni su'** è possibile specificare se si vuole che le informazioni sul componente aggiuntivo vengano visualizzate in una finestra di dialogo **Informazioni su**. Per visualizzare le informazioni, selezionare la casella di controllo **Sì, rendi disponibile la finestra 'Informazioni su' per il componente aggiuntivo**.

     Tra le informazioni che è possibile aggiungere alla finestra **Informazioni su** di Visual Studio sono inclusi il numero di versione, i dettagli sul supporto, i dati della licenza e così via.

15. Scegliere **Avanti**.

16. Le opzioni selezionate vengono visualizzate nella pagina **Riepilogo** per consentirne la revisione. Se il risultato è soddisfacente, scegliere **Fine** per creare il componente aggiuntivo. Se si vuole apportare delle modifiche, scegliere il pulsante **Indietro**.

     Vengono creati la nuova soluzione e il progetto e il file Connect.cs per il nuovo componente aggiuntivo viene visualizzato nell'editor di codice.

     Verrà aggiunto codice al file Connect.cs dopo la procedura riportata di seguito mediante la quale viene creato un controllo utente a cui farà riferimento questo progetto WebPerfTestResultsViewerAddin.

 Dopo aver creato un componente aggiuntivo, è necessario registrarlo con Visual Studio affinché possa essere attivato in **Gestione componenti aggiuntivi**. Questa operazione viene eseguita tramite un file XML con estensione addin.

 In questo file con estensione addin sono incluse le informazioni richieste da Visual Studio per visualizzare il componente aggiuntivo in **Gestione componenti aggiuntivi**. All'avvio, Visual Studio ricerca nel percorso dei file con estensione addin eventuali file con estensione addin disponibili. Se ne viene individuato uno, Visual Studio legge il file XML e fornisce a **Gestione componenti aggiuntivi** le informazioni necessarie per l'avvio del componente aggiuntivo quando viene fatto clic su quest'ultimo.

 Il file con estensione addin viene creato automaticamente quando si crea un componente aggiuntivo utilizzando la Creazione guidata componente aggiuntivo.

### <a name="add-in-file-locations"></a>Percorsi dei file del componente aggiuntivo

Tramite Creazione guidata componente aggiuntivo vengono create automaticamente due copie del file con estensione addin, come segue:

|**Percorso del file con estensione addin**|**Descrizione**|
|------------------------------|----------------------------|---------------------|
|Cartella radice del progetto|Utilizzato per la distribuzione del progetto del componente aggiuntivo. Incluso nel progetto per facilitare le modifiche e impostato sul percorso locale per la distribuzione di tipo XCopy.|
|Cartella del componente aggiuntivo|Utilizzata per l'esecuzione del componente aggiuntivo nell'ambiente di debug. Deve sempre indicare il percorso di output della configurazione della build corrente.|

## <a name="create-a-windows-form-control-library-project"></a>Creare un progetto Libreria di controlli Windows Form.

Il componente aggiuntivo per Visual Studio creato nella procedura precedente fa riferimento a un progetto Libreria di controlli Windows Form per creare un'istanza di una classe <xref:System.Windows.Forms.UserControl>.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Per creare un controllo da utilizzare nel Visualizzatore risultati test Web

1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi** e quindi **Nuovo progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.

2.  In **Modelli installati** espandere **Visual Basic** o **Visual C#** e selezionare **Windows**.

    > [!NOTE]
    > In questo argomento viene utilizzato Visual C# per il codice di esempio.

3.  Nell'elenco dei modelli selezionare **Libreria di controlli Windows Form**.

4.  In **Nome** digitare un nome per il componente aggiuntivo. Ad esempio, **WebPerfTestResultsViewerControl**.

5.  Scegliere **OK**.

     WebPerfTestResultsViewerControl del progetto della libreria di controlli Windows Form viene aggiunto in Esplora soluzioni e il file UserControl1.cs viene visualizzato nella modalità progettazione.

6.  Dalla casella degli strumenti trascinare un oggetto <xref:System.Windows.Forms.DataGridView> sulla superficie di userControl1.

7.  Fare clic sul glifo del tag azioni (![Glifo smart tag](../test/media/vs_winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) nell'angolo superiore destro di <xref:System.Windows.Forms.DataGridView> e attenersi alla procedura seguente:

    1.  Scegliere **Ancora nel contenitore padre**.

    2.  Deselezionare le caselle di controllo **Abilita aggiunta**, **Abilita modifica**, **Abilita eliminazione** e **Abilita riordinamento colonne**.

    3.  Scegliere **Aggiungi colonna**.

         Viene visualizzata la finestra di dialogo **Aggiungi colonna**.

    4.  Nell'elenco a discesa **Tipo** selezionare **DataGridViewTextBoxColumn**.

    5.  Deselezionare il testo "Column1" in **Testo intestazione**.

    6.  Scegliere **Aggiungi**.

    7.  Scegliere **Chiudi**.

8.  Nella finestra Proprietà impostare la proprietà **(Nome)** di <xref:System.Windows.Forms.DataGridView> su **resultControlDataGridView**.

9. Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare **Visualizza codice**.

     Il file UserControl1.cs verrà visualizzato nell'editor di codice.

10. Modificare il nome della classe istanziata <xref:System.Windows.Forms.UserControl> da UserContro1 a resultControl:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     Nella procedura seguente si aggiungerà codice al file Connect.cs del progetto WebPerfTestResultsViewerAddin che farà riferimento alla classe resultControl.

     Si aggiungerà ulteriore codice aggiuntivo al file Connect.cs in un secondo momento.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Aggiungere codice a WebPerfTestResultsViewerAddin

### <a name="to-add-code-to-the-visual-studio-add-in-to-extend-the-web-test-results-viewer"></a>Per aggiungere codice al componente aggiuntivo per Visual Studio per estendere il Visualizzatore risultati test Web

1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo **Riferimenti** nel progetto WebPerfTestResultsViewerAddin e selezionare **Aggiungi riferimento**.

2.  Nella finestra di dialogo **Aggiungi riferimento** scegliere la scheda **.NET**.

3.  Scorrere verso il basso e selezionare **Microsoft.VisualStudio.QualityTools.WebTestFramework** e **System.Windows.Forms**.

4.  Scegliere **OK**.

5.  Fare di nuovo clic con il pulsante destro del mouse sul nodo **Riferimenti** e selezionare **Aggiungi riferimento**.

6.  Nella finestra di dialogo **Aggiungi riferimento** scegliere la scheda **Sfoglia**.

7.  Scegliere l'elenco a discesa per **Cerca in**, passare a %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies e selezionare il file Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll.

8.  Scegliere **OK**.

9. Fare clic con il pulsante destro del mouse sul nodo del progetto WebPerfTestResultsViewerAddin e selezionare **Aggiungi riferimento**.

10. Nella finestra di dialogo **Aggiungi riferimento** scegliere la scheda **Progetti**.

11. In **Nome progetto** selezionare il progetto **WebPerfTestResultsViewerControl** e fare clic su **OK**.

12. Se il file Connect.cs non è ancora aperto, in Esplora soluzioni fare clic con il pulsante destro del mouse sul file **Connect.cs** nel progetto WebPerfTestResultsViewerAddin e selezionare **Visualizza codice**.

13. Nel file Connect.cs aggiungere le istruzioni Using seguenti:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Scorrere fino alla fine del file Connect.cs. È necessario aggiungere un elenco di GUID per l'oggetto <xref:System.Windows.Forms.UserControl> nel caso siano aperte più istanze del Visualizzatore risultati test prestazioni Web. Il codice utilizzato da questo elenco verrà aggiunto in un secondo momento.

     Un secondo elenco di stringhe viene utilizzato nel metodo OnDiscconection che verrà codificato in un secondo momento.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Il file Connect.cs consente di creare un'istanza di una classe denominata Connect dalla classe <xref:Extensibility.IDTExtensibility2> e di includere anche alcuni metodi per l'implementazione del componente aggiuntivo per Visual Studio. Uno dei metodi è OnConnection a cui viene notificato il caricamento del componente aggiuntivo. Nel metodo OnConnection verrà utilizzata la classe LoadTestPackageExt per creare il pacchetto di estendibilità per il Visualizzatore risultati test prestazioni Web. Aggiungere al metodo OnConnection il codice seguente:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Aggiungere il codice seguente alla classe Connect per creare il metodo WebTestResultViewerExt_WindowCreated per il gestore dell'evento loadTestPackageExt.WebTestResultViewerExt.WindowCreated aggiunto nel metodo OnConnection e per il metodo WindowCreated chiamato dal metodo WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Aggiungere il codice seguente alla classe Connect per creare il metodo WebTestResultViewer_SelectedChanged per il gestore dell'evento loadTestPackageExt.WebTestResultViewerExt.SelectionChanged aggiunto nel metodo OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Aggiungere il codice seguente alla classe Connect per creare il metodo WebTesResultViewer_WindowClosed per il gestore dell'evento per loadTestPackageExt.WebTestResultViewerExt.WindowClosed aggiunto nel metodo OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Ora che il codice per il componente aggiuntivo per Visual Studio è stato completato, è necessario aggiungere il metodo Update all'oggetto resultControl nel progetto WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Aggiungere codice a WebPerfTestResultsViewerControl

### <a name="to-add-code-to-the-user-control"></a>Per aggiungere codice al controllo utente

1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto WebPerfTestResultsViewerControl e selezionare **Proprietà**.

2.  Selezionare la scheda **Applicazione**, scegliere l'elenco a discesa **Framework di destinazione**, selezionare **.NET Framework 4** e chiudere Proprietà.

     Questa operazione è necessaria per supportare i riferimenti DLL necessari per l'estensione del Visualizzatore risultati test prestazioni Web.

3.  In Esplora soluzioni, nel progetto WebPerfTestResultsViewerControl fare clic con il pulsante destro del mouse sul nodo **Riferimenti** e selezionare **Aggiungi riferimento**.

4.  Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **.NET**.

5.  Scorrere verso il basso e selezionare **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6.  Scegliere **OK**.

7.  Nel file UserControl1.cs aggiungere le istruzioni Using seguenti:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8.  Aggiungere il metodo Update che viene chiamato e passato a un oggetto WebTestRequestResult dal metodo WebTestResultViewer_SelectedChanged di WebPerfTestResultsViewerAddin nel file Connect.cs. Il metodo Update consente di popolare l'oggetto DataGridView con varie proprietà passate a quest'ultimo nell'oggetto WebTestRequestResult.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-webperftestresultsvieweraddin-solution"></a>Compilare la soluzione WebPerfTestResultsViewerAddin

### <a name="to-build-the-solution"></a>Per compilare la soluzione

-   Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Registrare il componente aggiuntivo WebPerfTestResultsViewerAddin

### <a name="to-register-the-add-in-using-the-add-in-manager"></a>Per registrare il componente aggiuntivo utilizzando Gestione componenti aggiuntivi

1.  Scegliere **Gestione componenti aggiuntivi** dal menu **Strumenti**.

2.  Viene visualizzata la finestra di dialogo **Gestione componenti aggiuntivi**.

3.  Selezionare la casella di controllo per il componente aggiuntivo WebPerfTestResultsViewerAddin nella colonna **Componenti aggiuntivi disponibili** e deselezionare le caselle di controllo sotto le colonne **Avvio** e **Riga di comando**.

4.  Scegliere **OK**.

## <a name="run-the-web-performance-test-using-the-build-the-webperftestresultsvieweraddin-add-in"></a>Eseguire il test delle prestazioni Web utilizzando la compilazione del componente aggiuntivo WebPerfTestResultsViewerAddin

### <a name="to-run-the-new-vs-add-in-for-the-web-test-results-viewer"></a>Per eseguire il nuovo componente aggiuntivo per Visual Studio per il Visualizzatore risultati test prestazioni Web

1.  Eseguire il test delle prestazioni Web. Nel Visualizzatore risultati test prestazioni Web verrà visualizzata la nuova scheda del componente aggiuntivo WebPerfTestResultsViewerAddin, denominata Esempio.

2.  Scegliere la scheda per visualizzare le proprietà presentate nell'oggetto DataGridView.

## <a name="net-framework-security"></a>Sicurezza di .NET Framework

Per migliorare la sicurezza e impedire l'attivazione automatica di componenti aggiuntivi dannosi, Visual Studio offre impostazioni in una pagina **Opzioni** del menu Strumenti denominata **Sicurezza macro/componenti aggiuntivi**.

In questa pagina di opzioni è anche possibile specificare le cartelle in cui Visual Studio ricerca i file di registrazione con estensione AddIn. Limitando i percorsi in cui è possibile leggere i file di registrazione con estensione AddIn si migliora la sicurezza, evitando l'utilizzo non intenzionale di file con estensione AddIn dannosi.

 **Impostazioni di sicurezza dei componenti aggiuntivi**

 Le impostazioni disponibili nella pagina delle opzioni relative alla sicurezza dei componenti aggiuntivi sono le seguenti:

-   **Consenti caricamento componenti aggiuntivi.** Selezionato per impostazione predefinita. Quando selezionata, questa opzione consente il caricamento di componenti aggiuntivi in Visual Studio. In caso contrario, non è possibile caricare componenti aggiuntivi in Visual Studio.

-   **Consenti caricamento componenti aggiuntivi da URL.** Non selezionato per impostazione predefinita. Quando selezionata, questa opzione consente il caricamento di componenti aggiuntivi da siti Web esterni. In caso contrario, non è possibile caricare componenti aggiuntivi remoti in Visual Studio. Se per qualche motivo non è possibile eseguire il caricamento di un componente aggiuntivo, non potrà essere caricato dal Web. Questa impostazione controlla solo il caricamento della DLL del componente aggiuntivo. I file di registrazione Addin devono trovarsi sempre nel sistema locale.

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)