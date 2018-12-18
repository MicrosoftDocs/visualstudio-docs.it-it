---
title: Associare i controlli WPF a un set di dati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e2f3085be670a3344bc8239de5e4dfe4c8f11303
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Associare i controlli WPF a un set di dati
In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati. I controlli vengono associati a record di prodotto incapsulati in un set di dati. Si aggiungeranno inoltre i pulsanti per scorrere i prodotti e salvare le modifiche ai record di prodotto.

In questa procedura dettagliata vengono illustrate le attività seguenti:

- Creazione di un'applicazione WPF e di un set di dati generato dai dati nel database di esempio AdventureWorksLT.

- La creazione di un set di controlli con associazione a dati trascinando una tabella dati di **origini dati** finestra a una finestra di progettazione WPF.

- Creazione di pulsanti per spostarsi avanti e indietro tra i record di prodotto.

- Creazione di un pulsante che consente di salvare le modifiche apportate dagli utenti ai record di prodotto nella tabella dati e nell'origine dati sottostante.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisiti
Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).

Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

-   Set di dati e oggetti TableAdapter. Per ulteriori informazioni, vedere [strumenti Dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) e [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

-   Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Creare il progetto
 Creare un nuovo progetto WPF. Il progetto visualizzerà i record di prodotto.

#### <a name="to-create-the-project"></a>Per creare il progetto

1.  Avviare Visual Studio.

2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3.  Espandere **Visual Basic** o **Visual c#**, quindi selezionare **Windows**.

4.  Selezionare il **applicazione WPF** modello di progetto.

5.  Nel **nome** digitare `AdventureWorksProductsEditor` e fare clic su **OK**.

     Visual Studio crea il `AdventureWorksProductsEditor` progetto.

## <a name="create-a-dataset-for-the-application"></a>Creare un set di dati per l'applicazione
 Prima di creare controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungerlo al **origini dati** finestra. In questa procedura dettagliata viene creato un set di dati da usare come modello di dati.

#### <a name="to-create-a-dataset"></a>Per creare un set di dati

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

     Il **origini dati** verrà visualizzata la finestra.

2.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     Il **configurazione guidata origine dati** apre la procedura guidata.

3.  Nel **scegliere un tipo di origine dati** selezionare **Database**e quindi fare clic su **Avanti**.

4.  Nel **scegliere un modello di Database** selezionare **set di dati**, quindi fare clic su **successivo**.

5.  Nel **Seleziona connessione dati** pagina, selezionare una delle opzioni seguenti:

    -   Se una connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, selezionarlo e quindi fare clic su **Avanti**.

    -   Fare clic su **nuova connessione**e creare una connessione al database AdventureWorksLT.

6.  Nel **Salva stringa di connessione al File di configurazione dell'applicazione** pagina, selezionare il **Sì, Salva la connessione come** casella di controllo e quindi fare clic su **Avanti**.

7.  Nel **Seleziona oggetti di Database** espandere **tabelle**, quindi selezionare il **Product (SalesLT)** tabella.

8.  Scegliere **Fine**.

     Visual Studio aggiunge un nuovo `AdventureWorksLTDataSet.xsd` file al progetto e si aggiunge un oggetto corrispondente **AdventureWorksLTDataSet** elemento il **origini dati** finestra. Il `AdventureWorksLTDataSet.xsd` file definisce un set di dati tipizzato denominato `AdventureWorksLTDataSet` e un oggetto TableAdapter denominato `ProductTableAdapter`. Più avanti in questa procedura dettagliata, l'oggetto `ProductTableAdapter` verrà usato per riempire il set di dati con i dati e salvare nuovamente le modifiche nel database.

9. Compilare il progetto.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Modifica del metodo fill predefinito dell'oggetto TableAdapter
 Per riempire il set di dati con i dati, usare il metodo `Fill` dell'oggetto `ProductTableAdapter`. Per impostazione predefinita, il metodo `Fill` riempie `ProductDataTable` in `AdventureWorksLTDataSet` con tutte le righe di dati della tabella Product. È possibile modificare questo metodo in modo da restituire solo un subset di righe. Per questa procedura dettagliata, modificare il metodo `Fill` in modo da restituire solo di prodotti con foto.

#### <a name="to-load-product-rows-that-have-photos"></a>Per caricare le righe di prodotti con foto

1.  In **Esplora**, fare doppio clic su di `AdventureWorksLTDataSet.xsd` file.

     Viene aperto Progettazione DataSet.

2.  Nella finestra di progettazione, fare doppio clic su di **riempimento, GetData ()** query e selezionare **configura**.

     Il **TableAdapter Configuration** apre la procedura guidata.

3.  Nel **immettere un'istruzione SQL** pagina, aggiungere la clausola WHERE seguente dopo il `SELECT` istruzione nella casella di testo.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4.  Scegliere **Fine**.

## <a name="define-the-user-interface"></a>Definire l'interfaccia utente
 Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer. Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di scorrere e salvare le modifiche ai record di prodotti con questi pulsanti.

#### <a name="to-define-the-user-interface-of-the-window"></a>Per definire l'interfaccia utente della finestra

1.  In **Esplora**, fare doppio clic su MainWindow. Xaml.

     La finestra verrà aperta in WPF Designer.

2.  Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Compilare il progetto.

## <a name="create-data-bound-controls"></a>Creare controlli associati a dati
 Creare controlli che consentono di visualizzare i record cliente trascinando il `Product` tabella il **origini dati** finestra alla finestra di progettazione WPF.

#### <a name="to-create-data-bound-controls"></a>Per creare i controlli associati a dati

1.  Nel **origini dati** finestra, fare clic sul menu a discesa per la **prodotto** nodo e selezionare **dettagli**.

2.  Espandere il **prodotto** nodo.

3.  In questo esempio alcuni campi non verranno visualizzati, quindi fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **Nessuna**:

    -   ProductCategoryID

    -   ProductModelID

    -   ThumbnailPhotoFileName

    -   rowguid

    -   ModifiedDate

4.  Fare clic sul menu di riepilogo a discesa accanto al **ThumbNailPhoto** nodo e selezionare **immagine**.

    > [!NOTE]
    >  Per impostazione predefinita, gli elementi nel **origini dati** finestra che rappresentano immagini avere il controllo predefinito impostato su **Nessuno**. dal momento che le immagini vengono archiviate come matrici di byte nei database e le matrici di byte possono contenere qualsiasi elemento, da una matrice semplice di byte al file eseguibile di un'applicazione di grandi dimensioni.

5.  Dal **origini dati** finestra, trascinare il **prodotto** nodo nella riga della griglia sotto la riga che contiene i pulsanti.

     Visual Studio genera XAML che definisce un set di controlli associati ai dati di **prodotti** tabella. Genera inoltre il codice che carica i dati. Per ulteriori informazioni sulle XAML e codice generato, vedere [WPF di associare i controlli a dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6.  Nella finestra di progettazione, fare clic sulla casella di testo accanto al **ID prodotto** etichetta.

7.  Nel **proprietà** finestra, seleziona la casella di controllo accanto al **IsReadOnly** proprietà.

## <a name="navigating-product-records"></a>Esplorazione dei record di prodotto
 Aggiungere il codice che consente agli utenti di scorrere i record di prodotto usando il **\<** e **>** pulsanti.

#### <a name="to-enable-users-to-navigate-product-records"></a>Per consentire agli utenti di esplorare i record di prodotto

1.  Nella finestra di progettazione, fare doppio clic su di **<** pulsante nell'area della finestra.

     Visual Studio apre il file code-behind e crea un nuovo `backButton_Click` gestore eventi per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.

2.  Modificare il `Window_Loaded` gestore eventi, pertanto la `ProductViewSource`, `AdventureWorksLTDataSet`, e `AdventureWorksLTDataSetProductTableAdapter` dall'esterno del metodo e accessibili all'intero form. Dichiarare solo questi essere globali per il form e assegnarli all'interno di `Window_Loaded` gestore dell'evento simile al seguente:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3.  Aggiungere il codice seguente al gestore eventi `backButton_Click`:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4.  Tornare alla finestra di progettazione e fare doppio clic su di **>** pulsante.

5.  Aggiungere il codice seguente al gestore eventi `nextButton_Click`:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Salvare le modifiche ai record di prodotto
Aggiungere il codice che consente agli utenti di salvare le modifiche ai record di prodotto usando il **salvare modifiche** pulsante.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Per aggiungere la possibilità di salvare le modifiche ai record di prodotto

1.  Nella finestra di progettazione, fare doppio clic su di **salvare modifiche** pulsante.

     Visual Studio apre il file code-behind e crea un nuovo `saveButton_Click` gestore eventi per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.

2.  Aggiungere il codice seguente al gestore eventi `saveButton_Click`:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    >  Questo esempio usa il metodo `Save` di `TableAdapter` per salvare le modifiche. Tale approccio è appropriato a questa procedura dettagliata, in quanto viene modificata una sola tabella dati. Se è necessario salvare modifiche a più tabelle dati, è possibile usare in alternativa il metodo `UpdateAll` di `TableAdapterManager` generato da Visual Studio con il set di dati. Per ulteriori informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testare l'applicazione
 Compilare ed eseguire l'applicazione. Verificare che sia possibile visualizzare e aggiornare i record di prodotto.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1.  Premere **F5**.

     L'applicazione verrà compilata ed eseguita. Verificare quanto segue:

    -   Nelle caselle di testo vengono visualizzati i dati del primo record di prodotto contenente una foto. Questo prodotto include l'ID prodotto è 713 e il nome **Long-Sleeve Logo Jersey, S**.

    -   È possibile scegliere di **>** o **<** pulsanti per spostarsi tra gli altri record di prodotto.

2.  In uno dei record di prodotto, è possibile modificare il **dimensioni** valore e quindi fare clic su **salvare modifiche**.

3.  Chiudere l'applicazione e quindi riavviare l'applicazione premendo **F5** in Visual Studio.

4.  Passare al record di prodotto modificato e verificare che la modifica sia presente.

5.  Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:

-   Informazioni su come utilizzare il **origini dati** controlli finestra in Visual Studio per associare WPF ad altri tipi di origini dati. Per ulteriori informazioni, vedere [WPF di associare i controlli a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

-   Informazioni su come utilizzare il **origini dati** finestra in Visual Studio per visualizzare dati correlati (ovvero, i dati in una relazione padre-figlio) nei controlli WPF. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione di dati correlati in un'applicazione WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Panoramica sul data binding](/dotnet/framework/wpf/data/data-binding-overview)