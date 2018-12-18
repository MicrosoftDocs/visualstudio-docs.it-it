---
title: 'Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione di comportamento delle classi di entità'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f535f1d26120769ba2f321bff3ae41d78005d66f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione di comportamento delle classi di entità

Il [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornisce un'area di progettazione visiva per la creazione e modifica [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classi (classi di entità) che si basano su oggetti in un database. Utilizzando [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), è possibile utilizzare la tecnologia LINQ per accedere ai database SQL. Per altre informazioni, vedere [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/).

Per impostazione predefinita, la logica per eseguire gli aggiornamenti viene fornita dal runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Nel runtime vengono create istruzioni Insert, Update e Delete predefinite in base allo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Quando non si desidera usare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento e definire stored procedure specifiche per eseguire i comandi di inserimento, aggiornamento ed eliminazione necessari per l'uso dei dati nel database. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Inoltre, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure. Per ulteriori informazioni, vedere [personalizzazione di operazioni usando Stored procedure](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Questa procedura dettagliata richiede la disponibilità di **InsertCustomer**, **UpdateCustomer**, e **DeleteCustomer** stored procedure per il database Northwind.

In questa procedura dettagliata vengono forniti i passaggi da completare per eseguire l'override del comportamento in fase di esecuzione LINQ to SQL predefinito per salvare i dati in un database usando stored procedure.

In questa procedura dettagliata si apprenderà come eseguire le attività seguenti:

-   Creazione di una nuova applicazione Windows Form e aggiunta ad essa di un file [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].

-   Creazione di una classe di entità con mapping alla tabella Customers di Northwind.

-   Creazione dell'origine dati di un oggetto che fa riferimento alla classe LINQ to SQL Customer.

-   Creazione di un Windows Form che contiene un oggetto <xref:System.Windows.Forms.DataGridView> associato alla classe Customer.

-   Implementazione della funzionalità di salvataggio per il form.

-   Creazione di metodi <xref:System.Data.Linq.DataContext> mediante l'aggiunta di stored procedure a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

-   Configurazione della classe Customer in modo che utilizzi stored procedure per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .

       Verrà visualizzata una finestra dell'editor di query.

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Creazione di un'applicazione e aggiunta di classi LINQ to SQL

Poiché verranno usate classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] e verranno visualizzati i dati in un Windows Form, creare una nuova applicazione Windows Form e aggiungere un file di classi LINQ to SQL.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Per creare un nuovo progetto applicazione Windows Form che contiene LINQ to SQL classes

1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .

2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.

4. Denominare il progetto **UpdatingWithSProcsWalkthrough**, quindi scegliere **OK**.

     Il **UpdatingWithSProcsWalkthrough** progetto viene creato e aggiunto a **Esplora**.

4.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

5.  Fare clic su di **classi LINQ to SQL** modello e digitare **Northwind. dbml** nel **nome** casella.

6.  Fare clic su **Aggiungi**.

     Viene aggiunto al progetto un file di classi LINQ to SQL vuoto (Northwind.dbml) e viene aperto [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Creazione della classe di entità Customer e dell'origine dati di un oggetto

Creare [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] le classi che vengono mappate alle tabelle di database trascinando le tabelle da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Il risultato è rappresentato da classi di entità LINQ to SQL con mapping alle tabelle nel database. Dopo aver creato le classi di entità, è possibile usarle come origini dati di un oggetto analogamente alle altre classi che dispongono di proprietà pubbliche.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Per creare una classe di entità Customer e configurare un'origine dati con tale classe

1.  In **Esplora Server**/**Esplora Database**, individuare la tabella Customer nella versione SQL Server di database di esempio Northwind.

2.  Trascinare il **clienti** nodo da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] area.

     Una classe di entità denominata **cliente** viene creato. che presenta proprietà corrispondenti alle colonne della tabella Customers. La classe di entità viene denominata **cliente** (non **clienti**) perché rappresenta un singolo cliente dalla tabella Customers.

    > [!NOTE]
    >  Questo comportamento di ridenominazione viene chiamato *pluralizzazione*. Può essere attivata o disattivata [la finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md). Per ulteriori informazioni, vedere [procedura: attivare e disattivare (O/R Designer) la pluralizzazione](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3.  Nel **compilare** menu, fare clic su **Compila UpdatingwithSProcsWalkthrough** per compilare il progetto.

4.  Scegliere **Mostra origini dati** dal menu **Dati**.

5.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

6.  Fare clic su **oggetto** sul **scegliere un tipo di origine dati** pagina e quindi fare clic su **Avanti**.

7.  Espandere il **UpdatingwithSProcsWalkthrough** nodo e individuare e selezionare il **cliente** classe.

    > [!NOTE]
    >  Se il **cliente** classe non è disponibile, annullare la procedura guidata, compilare il progetto e rieseguire la procedura guidata.
8.  Fare clic su **fine** per creare l'origine dati e aggiungere il **cliente** la classe di entità per il **origini dati** finestra.

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Creazione di un controllo DataGridView per visualizzare i dati dei clienti in un Windows Form

Creare controlli associati alle classi di entità trascinando [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] elementi dall'origine dati di **origini dati** finestra in un Windows Form.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Per aggiungere controlli associati alle classi di entità

1.  Aprire Form1 nella visualizzazione Progettazione.

2.  Dal **origini dati** finestra, trascinare il **cliente** nodo in Form1.

    > [!NOTE]
    > Per visualizzare il **origini dati** finestra, fare clic su **Mostra origini dati** sul **dati** menu.

3.  Aprire Form1 nell'editor del codice.

4.  Aggiungere al form il seguente codice, che verrà applicato all'intero form, all'esterno di un metodo specifico ma all'interno della classe Form1:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5.  Creare un gestore eventi per l'evento `Form_Load` e aggiungere il seguente codice al gestore:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implementing-save-functionality"></a>Implementazione della funzionalità di salvataggio

Per impostazione predefinita, il pulsante Salva non è abilitato e la funzionalità di salvataggio non è implementata. Inoltre, quando vengono creati controlli associati a dati per le origini dati di un oggetto, non viene aggiunto codice automaticamente per salvare i dati modificati nel database. Contenuto della sezione viene illustrato come abilitare il pulsante Salva e implementare la funzionalità di salvataggio per gli oggetti [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].

### <a name="to-implement-save-functionality"></a>Per implementare la funzionalità di salvataggio

1.  Aprire Form1 nella visualizzazione Progettazione.

2.  Selezionare Salva pulsante il **CustomerBindingNavigator** (il pulsante con l'icona del disco floppy).

3.  Nel **proprietà** finestra, impostare il **abilitato** proprietà **True**.

4.  Fare doppio clic sul pulsante Salva per creare un gestore eventi e passare all'editor del codice.

5.  Aggiungere il seguente codice nel gestore eventi del pulsante Salva:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Override del comportamento predefinito per l'esecuzione degli aggiornamenti (comandi di inserimento, aggiornamento ed eliminazione)

### <a name="to-override-the-default-update-behavior"></a>Per eseguire l'override del comportamento di aggiornamento predefinito

1.  Aprire il file LINQ to SQL in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Fare doppio clic su di **Northwind. dbml** file **Esplora**.)

2.  In **Esplora Server**/**Esplora Database**, espandere i database Northwind **Stored procedure** nodo e individuare il  **InsertCustomers**, **UpdateCustomers**, e **DeleteCustomers** stored procedure.

3.  Trascinare tutte e tre le stored procedure in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

     Le stored procedure vengono aggiunte al riquadro dei metodi come metodi <xref:System.Data.Linq.DataContext>. Per ulteriori informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Selezionare il **cliente** classe di entità di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

5.  Nel **proprietà** finestra, seleziona il **inserire** proprietà.

6.  Fare clic sui puntini di sospensione (...) accanto a **Usa fase di esecuzione** per aprire la **Configura comportamento** la finestra di dialogo.

7.  Selezionare **personalizzare**.

8.  Selezionare il **InsertCustomers** metodo il **Personalizza** elenco.

9. Fare clic su **applica** per salvare la configurazione per la classe e al comportamento selezionati.

    > [!NOTE]
    >  È possibile continuare a configurare il comportamento per ogni combinazione di classe/comportamento purché faccia clic su **applica** dopo ogni modifica apportata. Se si modifica la classe o il comportamento prima di scegliere **applica**, una finestra di dialogo di avviso offre la possibilità di applicare le modifiche verrà visualizzati.

10. Selezionare **aggiornamento** nel **comportamento** elenco.

11. Selezionare **personalizzare**.

12. Selezionare il **UpdateCustomers** metodo il **Personalizza** elenco.

     Controllare l'elenco di **gli argomenti del metodo** e **proprietà della classe** e notare che sono disponibili due **gli argomenti del metodo** e due **proprietà della classe**per alcune colonne nella tabella. In tal modo, vengono facilitati il rilevamento delle modifiche e la creazione di istruzioni che verifichino la presenza di eventuali violazioni di concorrenza.

13. Mappa di **Original_CustomerID** argomento del metodo per il **CustomerID (Original)** proprietà della classe.

    > [!NOTE]
    >  Per impostazione predefinita, verrà eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se i nomi di proprietà vengono modificati e non vi è più corrispondenza tra quelli della tabella e quelli della classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui Progettazione relazionale oggetti non sia in grado di determinare il mapping corretto. Inoltre, se gli argomenti del metodo non dispone di proprietà di classe valide per eseguire il mapping, è possibile impostare il **proprietà della classe** valore **(nessuno)**.

14. Fare clic su **applica** per salvare la configurazione per la classe e al comportamento selezionati.

15. Selezionare **eliminare** nel **comportamento** elenco.

16. Selezionare **personalizzare**.

17. Selezionare il **DeleteCustomers** metodo il **Personalizza** elenco.

18. Mappa di **Original_CustomerID** argomento del metodo per il **CustomerID (Original)** proprietà della classe.

19. Fare clic su **OK**.

> [!NOTE]
> Sebbene non sia un problema per questa procedura dettagliata, è opportuno notare che [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gestisce i valori generati dal database automaticamente per le colonne identity (incremento automatico), rowguidcol (GUID generato dal database) e timestamp durante le operazioni di inserimento e aggiornamento. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="testing-the-application"></a>Test dell'applicazione

Eseguire nuovamente l'applicazione per verificare che il **UpdateCustomers** stored procedure aggiorna correttamente il record del cliente nel database.

### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1.  Premere F5.

2.  Modificare un record nella griglia per testare il comportamento di Update.

3.  Aggiungere un nuovo record per testare il comportamento di Insert.

4.  Fare clic sul pulsante Salva per salvare le modifiche nel database.

5.  Chiudere il form.

6.  Premere F5 e verificare che il record aggiornato e quello appena inserito siano stati salvati in modo permanente.

7.  Eliminare il nuovo record creato nel passaggio 3 per testare il comportamento di Delete.

8.  Fare clic sul pulsante Salva per inviare le modifiche e rimuovere il record eliminato dal database.

9. Chiudere il form.

10. Premere F5 e verificare che il record eliminato sia stato rimosso dal database.

    > [!NOTE]
    > Se l'applicazione Usa SQL Server Express Edition in base al valore di **copia nella Directory di Output di** proprietà del file di database, le modifiche potrebbero non viene visualizzata quando si preme F5 nel passaggio 10.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo la creazione delle classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. È possibile apportare alcuni miglioramenti a questa applicazione, tra cui:

- Implementazione del controllo della concorrenza durante gli aggiornamenti. Per informazioni, vedere [la concorrenza ottimistica: Panoramica](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Aggiunta di query LINQ per filtrare i dati. Per informazioni, vedere [Introduzione alle query LINQ (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Query LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)