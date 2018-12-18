---
title: Associare i controlli WPF a un servizio dati WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d02b86991dd7ea712ceba2db06f90fbc776b4088
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Associare i controlli WPF a un servizio dati WCF

In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati. I controlli vengono associati a record cliente incapsulati in un'istanza di [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]. Verranno inoltre aggiunti i pulsanti che i clienti possono usare per visualizzare e aggiornare i record.

In questa procedura dettagliata vengono illustrate le attività seguenti:

- Creazione di un modello Entity Data Model generato dai dati nel database di esempio AdventureWorksLT.

- Creazione di un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] che espone i dati in Entity Data Model in un'applicazione WPF.

- Creazione di un set di controlli con associazione a dati trascinando elementi dal **origini dati** finestra alla finestra di progettazione WPF.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record cliente.

- Creazione di un pulsante che consente di salvare le modifiche ai dati nei controlli di [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] e l'origine dati sottostante.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisiti
Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).

Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

-   WCF Data Services. Per ulteriori informazioni, vedere [Panoramica](/dotnet/framework/data/wcf/wcf-data-services-overview).

-   Modelli di dati in [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

-   Modelli di Entity Data Model e ADO.NET Entity Framework. Per ulteriori informazioni, vedere [Panoramica di Entity Framework](/dotnet/framework/data/adonet/ef/overview).

-   Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Creare il progetto di servizio
Avviare la procedura dettagliata creando un progetto per un'istanza di [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

### <a name="to-create-the-service-project"></a>Per creare il progetto di servizio

1.  Avviare Visual Studio.

2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3.  Espandere **Visual c#** o **Visual Basic**, quindi selezionare **Web**.

4.  Selezionare il modello di progetto **Applicazione Web ASP.NET**.

5.  Nel **nome** digitare `AdventureWorksService` e fare clic su **OK**.

     Visual Studio crea il `AdventureWorksService` progetto.

6.  In **Esplora**, fare doppio clic su **Default.aspx** e selezionare **eliminare**. Questo file non è necessario per la procedura dettagliata.

## <a name="create-an-entity-data-model-for-the-service"></a>Creare un Entity Data Model per il servizio
Per esporre i dati in un'applicazione usando un'istanza di [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], è necessario definire un modello di dati per il servizio. Il [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] supporta due tipi di modelli di data: Entity Data Model e modelli di dati personalizzati che vengono definiti utilizzando oggetti common language runtime (CLR) che implementano il <xref:System.Linq.IQueryable%601> interfaccia. In questa procedura dettagliata, viene creato un modello Entity Data Model per il modello di dati.

### <a name="to-create-an-entity-data-model"></a>Per creare un modello Entity Data Model

1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2.  Nell'elenco Modelli installati, fare clic su **dati**, quindi selezionare il **ADO.NET Entity Data Model** elemento del progetto.

3.  Modificare il nome in `AdventureWorksModel.edmx`, fare clic su **Aggiungi**.

     Il **Entity Data Model** apre la procedura guidata.

4.  Nel **Scegli contenuto Model** pagina, fare clic su **genera da database**, fare clic su **Avanti**.

5.  Nel **Seleziona connessione dati** pagina, selezionare una delle opzioni seguenti:

    -   Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.

    -   Fare clic su **nuova connessione**e creare una connessione al database AdventureWorksLT.

6.  Nel **Seleziona connessione dati** pagina, assicurarsi che il **Salva entità di impostazioni di connessione in App. config come** opzione è selezionata e quindi fare clic su **Avanti**.

7.  Nel **Seleziona oggetti di Database** espandere **tabelle**, quindi selezionare il **SalesOrderHeader** tabella.

8.  Scegliere **Fine**.

## <a name="create-the-service"></a>Creare il servizio
Creare un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] per esporre i dati in Entity Data Model in un'applicazione WPF.

### <a name="to-create-the-service"></a>Per creare il servizio

1.  Nel **progetto** dal menu **Aggiungi nuovo elemento**.

2.  Nell'elenco Modelli installati, fare clic su **Web**, quindi selezionare il **servizio dati WCF** elemento del progetto.

3.  Nel **nome** digitare `AdventureWorksService.svc`, fare clic su **Aggiungi**.

     Visual Studio aggiunge il `AdventureWorksService.svc` al progetto.

## <a name="configure-the-service"></a>Configurare il servizio
È necessario configurare il servizio in modo da usare il modello Entity Data Model creato.

### <a name="to-configure-the-service"></a>Per configurare il servizio

1.  Nel `AdventureWorks.svc` file di codice, sostituire il `AdventureWorksService` classe dichiarazione con il codice seguente.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Questo codice aggiorna il `AdventureWorksService` classe, in modo che derivi da un <xref:System.Data.Services.DataService%601> che usa il `AdventureWorksLTEntities` oggetto classe di contesto del modello Entity Data Model. Aggiorna inoltre il metodo `InitializeService` per consentire ai client del servizio l'accesso completo in lettura/scrittura all'entità `SalesOrderHeader`.

2.  Compilare il progetto e verificare che non siano presenti errori.

## <a name="create-the-wpf-client-application"></a>Creare l'applicazione client WPF
Per visualizzare i dati di [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], creare una nuova applicazione WPF con un'origine dati basata sul servizio. Più avanti in questa procedura dettagliata, verranno aggiunti all'applicazione i controlli associati a dati.

### <a name="to-create-the-wpf-client-application"></a>Per creare l'applicazione client WPF

1.  In **Esplora**pulsante destro del mouse sul nodo della soluzione, fare clic su **Aggiungi**e selezionare **nuovo progetto**.

2.  Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** o **Visual Basic**, quindi selezionare **Windows**.

3.  Selezionare il **applicazione WPF** modello di progetto.

4.  Nel **nome** digitare `AdventureWorksSalesEditor`, fare clic su **OK**.

     Visual Studio aggiunge il `AdventureWorksSalesEditor` progetto alla soluzione.

5.  Scegliere **Mostra origini dati** dal menu **Dati**.

     Il **origini dati** verrà visualizzata la finestra.

6.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     Il **configurazione guidata origine dati** apre la procedura guidata.

7.  Nel **scegliere un tipo di origine dati** pagina della procedura guidata, selezionare **servizio**, quindi fare clic su **Avanti**.

8.  Nel **Aggiungi riferimento al servizio** la finestra di dialogo, fare clic su **Discover**.

     Visual Studio cerca i servizi disponibili nella soluzione corrente e aggiunge `AdventureWorksService.svc` all'elenco dei servizi disponibili il **servizi** casella.

9. Nel **Namespace** digitare `AdventureWorksService`.

10. Nel **servizi** fare clic su **AdventureWorksService.svc**, quindi fare clic su **OK**.

     Visual Studio Scarica le informazioni del servizio e quindi restituisce per la **configurazione guidata origine dati** procedura guidata.

11. Nel **Aggiungi riferimento al servizio** pagina, fare clic su **fine**.

     Visual Studio aggiunge i nodi che rappresentano i dati restituiti dal servizio per il **origini dati** finestra.

## <a name="define-the-user-interface-of-the-window"></a>Definire l'interfaccia utente della finestra
Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di visualizzare e aggiornare i record delle vendite tramite questi pulsanti.

### <a name="to-create-the-window-layout"></a>Per creare il layout della finestra

1.  In **Esplora**, fare doppio clic su **MainWindow. XAML**.

     La finestra verrà aperta in WPF Designer.

2.  Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Compilare il progetto.

## <a name="create-the-data-bound-controls"></a>Creare i controlli con associazione a dati
Creare controlli che consentono di visualizzare i record cliente trascinando il `SalesOrderHeaders` nodo dal **origini dati** finestra alla finestra di progettazione.

### <a name="to-create-the-data-bound-controls"></a>Per creare i controlli associati a dati

1.  Nel **origini dati** finestra, fare clic sul menu a discesa per la **SalesOrderHeaders** nodo e selezionare **dettagli**.

2.  Espandere il **SalesOrderHeaders** nodo.

3.  In questo esempio alcuni campi non verranno visualizzati, quindi fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **Nessuna**:

    -   **CreditCardApprovalCode**

    -   **ModifiedDate**

    -   **OnlineOrderFlag**

    -   **RevisionNumber**

    -   **rowguid**

    Questa azione impedisce a Visual Studio di creare i controlli associati a dati per questi nodi nel passaggio successivo. Questa procedura dettagliata, si presuppone che l'utente finale non debba visualizzare questi dati.

4.  Dal **origini dati** finestra, trascinare il **SalesOrderHeaders** nodo nella riga della griglia sotto la riga che contiene i pulsanti.

     Visual Studio genera XAML e codice che crea un set di controlli associati ai dati di **prodotto** tabella. Per ulteriori informazioni sulle XAML e codice generato, vedere [WPF di associare i controlli a dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5.  Nella finestra di progettazione, fare clic sulla casella di testo accanto al **ID cliente** etichetta.

6.  Nel **proprietà** finestra, seleziona la casella di controllo accanto al **IsReadOnly** proprietà.

7.  Impostare il **IsReadOnly** proprietà per ognuna delle caselle di testo seguente:

    -   **Numero di ordine di acquisto**

    -   **ID di ordine di vendita**

    -   **Numero di ordine di vendita**

## <a name="load-the-data-from-the-service"></a>Caricare i dati dal servizio
Utilizzare l'oggetto proxy del servizio per caricare i dati di vendita dal servizio. Assegnare quindi i dati restituiti all'origine dati per il <xref:System.Windows.Data.CollectionViewSource> nella finestra WPF.

### <a name="to-load-the-data-from-the-service"></a>Per caricare i dati dal servizio

1.  Nella finestra di progettazione, per creare il `Window_Loaded` gestore dell'evento, fare doppio clic sul testo: **MainWindow**.

2.  Sostituire il gestore eventi con il codice seguente. Assicurarsi di sostituire il *localhost* indirizzo in questo codice con l'indirizzo dell'host locale nel computer di sviluppo.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Esplorare i record delle vendite
Aggiungere il codice che consente agli utenti di scorrere i record delle vendite usando il **\<** e **>** pulsanti.

### <a name="to-enable-users-to-navigate-sales-records"></a>Per consentire agli utenti di esplorare i record delle vendite

1.  Nella finestra di progettazione, fare doppio clic su di **<** pulsante nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo `backButton_Click` gestore eventi per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.

2.  Aggiungere il codice seguente al gestore eventi `backButton_Click` generato:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3.  Tornare alla finestra di progettazione e fare doppio clic su di **>** pulsante.

     Visual Studio apre il file code-behind e crea un nuovo `nextButton_Click` gestore eventi per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.

4.  Aggiungere il codice seguente al gestore eventi `nextButton_Click` generato:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="saving-changes-to-sales-records"></a>Salvare le modifiche ai record delle vendite
Aggiungere il codice che consente agli utenti di visualizzare e salvare le modifiche ai record delle vendite usando il **salvare modifiche** pulsante.

### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Per aggiungere la possibilità di salvare le modifiche ai record delle vendite

1.  Nella finestra di progettazione, fare doppio clic su di **Salva modifiche** pulsante.

     Visual Studio apre il file code-behind e crea un nuovo `saveButton_Click` gestore eventi per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.

2.  Aggiungere il codice seguente al gestore eventi `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="testing-the-application"></a>Test dell'applicazione
Compilare ed eseguire l'applicazione per verificare che sia possibile visualizzare e aggiornare i record cliente.

### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1.  In **compilare** menu, fare clic su **Compila soluzione**. Verificare che la soluzione venga compilata senza errori.

2.  Premere **Ctrl + F5**.

     Visual Studio avvia il **AdventureWorksService** progetto, senza eseguirne il debug.

3.  In **Esplora**, fare doppio clic su di **AdventureWorksSalesEditor** progetto.

4.  Nel menu di scelta rapida in **Debug**, fare clic su **Avvia nuova istanza**.

     Verrà eseguita l'applicazione. Verificare quanto segue:

    -   Campi di dati diversi dal primo record delle vendite, con l'ID dell'ordine di vendita di visualizzare le caselle di testo **71774**.

    -   È possibile scegliere di **>** o **<** pulsanti per spostarsi tra gli altri record delle vendite.

5.  In uno dei record delle vendite, digitare un testo nel **commento** casella e quindi fare clic su **salvare modifiche**.

6.  Chiudere l'applicazione, quindi avviarla di nuovo da Visual Studio.

7.  Passare al record delle vendite modificato e verificare che la modifica sia presente dopo avere chiuso e riaperto l'applicazione.

8.  Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:

-   Informazioni su come utilizzare il **origini dati** controlli finestra in Visual Studio per associare WPF ad altri tipi di origini dati. Per ulteriori informazioni, vedere [WPF di associare i controlli a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md).

-   Informazioni su come utilizzare il **origini dati** finestra in Visual Studio per visualizzare dati correlati (ovvero, i dati in una relazione padre-figlio) nei controlli WPF. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione di dati correlati in un'applicazione WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Panoramica WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Panoramica di Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Data Binding Panoramica (.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)