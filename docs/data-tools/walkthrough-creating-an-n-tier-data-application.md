---
title: "Procedura dettagliata: creazione di un'applicazione dati a più livelli"
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b62c39ea1c261612568cb0d228c9082fa2d19070
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Procedura dettagliata: creazione di un'applicazione dati a più livelli
*A più livelli* le applicazioni di dati sono applicazioni con accesso ai dati sono suddivisi in più livelli logici, o *livelli*. La separazione dei componenti dell'applicazione in livelli discreti aumenta la manutenibilità e la scalabilità dell'applicazione mediante l'adozione semplificata di nuove tecnologie che possono essere applicate a un singolo livello senza la necessità di riprogettare l'intera soluzione. L'architettura a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il livello intermedio include in genere un livello di accesso ai dati, un livello di logica di business e componenti condivisi quali l'autenticazione e la convalida. Il livello dati include un database relazionale. Le applicazioni a più livelli in genere archiviano le informazioni riservate nel livello di accesso ai dati del livello intermedio per mantenere l'isolamento dagli utenti finali che accedono al livello di presentazione. Per ulteriori informazioni, vedere [panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md).

Per separare i vari livelli in un'applicazione a più livelli, è possibile creare progetti discreti per ogni livello da includere nell'applicazione. I dataset tipizzati contengono una proprietà `DataSet Project` che determina in quali progetti deve essere inserito il codice generato del dataset e di `TableAdapter`.

Questa procedura dettagliata viene illustrato come separare dataset e `TableAdapter` codice in progetti di libreria di classi discreti usando il **Progettazione Dataset**. Dopo che si separano i dataset e TableAdapter codice, si creerà un [servizi Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) servizio per effettuare chiamate nel livello di accesso ai dati. Infine, si creerà un'applicazione Windows Forms come livello di presentazione. Questo livello accede ai dati dal servizio dati.

Durante questa procedura dettagliata, verranno eseguiti i passaggi seguenti:

-   Creare una nuova soluzione a più livelli che contiene più progetti.

-   Aggiungere due progetti di libreria di classi alla soluzione a più livelli.

-   Creare un dataset tipizzato utilizzando il **configurazione guidata origine dati**.

-   Separare generato [TableAdapter](create-and-configure-tableadapters.md) e il codice del dataset in progetti discreti.

-   Creare un servizio Windows Communication Foundation (WCF) per effettuare chiamate nel livello di accesso ai dati.

-   Creare funzioni nel servizio per recuperare i dati dal livello di accesso ai dati.

-   Creare un'applicazione Windows Form come livello di presentazione.

-   Creare i controlli Windows Form associati all'origine dati.

-   Scrivere il codice per popolare le tabelle dati.

![collegamento alla trasmissione video](../data-tools/media/playvideo.gif "PlayVideo") per una versione video di questo argomento, vedere [procedura Video: creazione di un'applicazione dati a più livelli](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Prerequisiti
Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **lo sviluppo desktop .NET** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .

       Verrà visualizzata una finestra dell'editor di query.

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Creazione della soluzione a più livelli e della libreria di classi per contenere il dataset (DataEntityTier)
 Il primo passaggio di questa procedura dettagliata prevede la creazione di una soluzione e di due progetti di libreria di classi. La prima libreria di classi conterrà il dataset (la classe DataSet tipizzato e gli oggetti DataTable generati che conterranno i dati dell'applicazione). Il progetto viene usato come livello di entità di dati dell'applicazione e di norma si trova nel livello intermedio. Datasetis usato per creare il set di dati iniziale e separare automaticamente il codice in due librerie.

> [!NOTE]
>  Assicurarsi di assegnare un nome di progetto e soluzione correttamente prima di scegliere **OK**. In tal modo sarà più semplice completare questa procedura dettagliata.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Per creare la soluzione a più livelli e la libreria di classi DataEntityTier

1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .

2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.

3. Nel riquadro centrale, selezionare il **libreria di classi** tipo di progetto.

4. Denominare il progetto **DataEntityTier**.

5. Denominare la soluzione **NTierWalkthrough**, quindi scegliere **OK**.

     Una soluzione NTierWalkthrough che contiene il progetto DataEntityTier viene creata e aggiunto a **Esplora**.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Creazione della libreria di classi per contenere gli oggetti TableAdapter (DataAccessTier)
 Il passaggio successivo alla creazione del progetto DataEntityTier prevede la creazione di un altro progetto di libreria di classi. Questo progetto conterrà generato `TableAdapter`s e viene chiamato il *livello accesso dati* dell'applicazione. Tale livello contiene le informazioni richieste per la connessione al database e in genere si trova nel livello intermedio.

#### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Per creare una libreria di classi separato per gli oggetti TableAdapter

1.  Pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliere **Aggiungi**, **nuovo progetto...** .

2.  Nel **nuovo progetto** la finestra di dialogo, nel riquadro centrale seleziona **libreria di classi**.

3.  Denominare il progetto **DataAccessTier** e scegliere **OK**.

     Il progetto DataAccessTier viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="creating-the-dataset"></a>Creazione del set di dati
 Il passaggio successivo consiste nella creazione di un dataset tipizzato. I dataset tipizzati sono creati con la classe DataSet (comprese le classi DataTable) e le classi `TableAdapter`, in un singolo progetto. Tutte le classi vengono generate in un unico file. Quando il dataset e gli oggetti `TableAdapter` vengono separati in progetti diversi, è la classe DataSet che viene spostata nell'altro progetto, mentre le classi `TableAdapter` restano nel progetto originale. Di conseguenza, è necessario creare il dataset nel progetto che alla fine conterrà gli oggetti `TableAdapter` (il progetto DataAccessTier). Si creerà il set di dati utilizzando il **configurazione guidata origine dati**.

> [!NOTE]
>  Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni su come impostare il database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).

#### <a name="to-create-the-dataset"></a>Per creare il dataset

1.  Selezionare DataAccessTier in **Esplora**.

2.  Nel **dati** dal menu **Mostra origini dati**.

3.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati**.

4.  Nel **scegliere un tipo di origine dati** selezionare **Database** e quindi selezionare **Avanti**.

5.  Nel **Seleziona connessione dati** pagina, effettuare una delle azioni seguenti:

     Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

     oppure

     Selezionare **nuova connessione** per aprire la **Aggiungi connessione** la finestra di dialogo.

6.  Se il database richiede una password, selezionare l'opzione per includere dati riservati, quindi fare clic **Avanti**.

    > [!NOTE]
    >  Se è stato selezionato un file di database locale al posto della connessione a SQL Server, potrebbe venire richiesto di aggiungere il file al progetto. Scegliere **Sì** per aggiungere il file di database al progetto.

7.  Selezionare **Avanti** sul **Salva stringa di connessione al File di configurazione dell'applicazione** pagina.

8.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database** .

9.  Selezionare le caselle di controllo per il **clienti** e **ordini** le tabelle e quindi scegliere **fine**.

     NorthwindDataSet viene aggiunto al progetto DataAccessTier e viene visualizzato nel **origini dati** finestra.

## <a name="separating-the-tableadapters-from-the-dataset"></a>Separazione degli oggetti TableAdapter dal dataset
 Dopo avere creato il dataset, separare la classe DataSet generata dagli oggetti TableAdapter. A questo scopo, impostare il **progetto DataSet** proprietà sul nome del progetto in cui archiviare la separata classe dataset.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Per separare gli oggetti TableAdapter dal dataset

1.  Fare doppio clic su **NorthwindDataSet.xsd** in **Esplora** per aprire il dataset nel **Progettazione Dataset**.

2.  Selezionare un'area vuota della finestra di progettazione.

3.  Individuare il **progetto DataSet** nodo il **proprietà** finestra.

4.  Nel **progetto DataSet** elenco, selezionare **DataEntityTier**.

5.  Scegliere **Compila soluzione** dal menu **Compila**.

 Il dataset e gli oggetti TableAdapter sono separati nei due progetti di libreria di classi. Il progetto che originalmente conteneva l'intero dataset (DataAccessTier) ora contiene solo gli oggetti TableAdapter. Il progetto definito nella **progetto DataSet** proprietà (DataEntityTier) contiene il dataset tipizzato: VB (o NorthwindDataSet).

> [!NOTE]
>  Quando si separano i DataSet e TableAdapter (impostando il **progetto DataSet** proprietà), classi parziali del dataset esistenti nel progetto non vengono spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.

## <a name="creating-a-new-service-application"></a>Creazione di una nuova applicazione di servizio
Questa procedura dettagliata viene illustrato come accedere a livello di accesso ai dati tramite un servizio WCF, è pertanto possibile crearne una nuova applicazione di servizio WCF.

#### <a name="to-create-a-new-wcf-service-application"></a>Per creare una nuova applicazione del servizio WCF

1.  Pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliere **Aggiungi**, **nuovo progetto...** .

2.  Nel **nuovo progetto** la finestra di dialogo, nel riquadro a sinistra, seleziona **WCF**.  Nel riquadro centrale, selezionare **libreria di servizi WCF**.

3.  Denominare il progetto **DataService** e selezionare **OK**.

     Il progetto DataService viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Creazione di metodi nel livello di accesso ai dati per restituire i dati dei clienti e degli ordini
 Il servizio dati deve chiamare due metodi nel livello di accesso ai dati: GetCustomers e GetOrders. Questi metodi restituiscono le tabelle Customers e Orders di Northwind. Creare i metodi GetCustomers e GetOrders nel progetto DataAccessTier.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Per creare un metodo nel livello di accesso ai dati per restituire la tabella Customers

1.  In **Esplora**, fare doppio clic su NorthwindDataset.xsd per aprire il set di dati.

2.  Fare doppio clic su CustomersTableAdapter e fare clic su **Aggiungi Query**.

3.  Nel **scegliere un tipo di comando** , mantenere il valore predefinito di **Usa istruzioni SQL** e fare clic su **Avanti**.

4.  Nel **scegliere un tipo di Query** , mantenere il valore predefinito di **SELECT che restituisce righe** e fare clic su **Avanti**.

5.  Nel **specificare un'istruzione SQL SELECT** pagina, lasciare la query predefinita e fare clic su **Avanti**.

6.  Nel **scegliere i metodi per generare** , digitare **GetCustomers** per il **nome del metodo** nel **Restituisci un DataTable** sezione.

7.  Scegliere **Fine**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Per creare un metodo nel livello di accesso ai dati per restituire la tabella Orders

1.  Fare doppio clic su OrdersTableAdapter e fare clic su **Aggiungi Query**.

2.  Nel **scegliere un tipo di comando** , mantenere il valore predefinito di **Usa istruzioni SQL** e fare clic su **Avanti**.

3.  Nel **scegliere un tipo di Query** , mantenere il valore predefinito di **SELECT che restituisce righe** e fare clic su **Avanti**.

4.  Nel **specificare un'istruzione SQL SELECT** pagina, lasciare la query predefinita e fare clic su **Avanti**.

5.  Nel **scegliere i metodi per generare** , digitare **GetOrders** per il **nome del metodo** nel **Restituisci un DataTable** sezione.

6.  Scegliere **Fine**.

7.  Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Aggiunta di un riferimento ai livelli di entità di dati e di accesso ai dati nel servizio dati
 Dal momento che il servizio dati richiede le informazioni dal dataset e dagli oggetti TableAdapter, è necessario aggiungere riferimenti ai progetti DataEntityTier e DataAccessTier.

#### <a name="to-add-references-to-the-data-service"></a>Per aggiungere riferimenti al servizio dati

1.  Fare doppio clic su DataService in **Esplora** e fare clic su **Aggiungi riferimento**.

2.  Fare clic su di **progetti** nella scheda il **Aggiungi riferimento** la finestra di dialogo.

3.  Selezionare sia la **DataAccessTier** e **DataEntityTier** progetti.

4.  Fare clic su **OK**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Aggiunta di funzioni al servizio per chiamare i metodi GetCustomers e GetOrders nel livello di accesso ai dati
 Ora che il livello di accesso ai dati contiene i metodi per restituire i dati, creare i metodi nel servizio dati per chiamare i metodi nel livello di accesso ai dati.

> [!NOTE]
>  Per i progetti C# è necessario aggiungere un riferimento all'assemby `System.Data.DataSetExtensions` per eseguire la compilazione del codice seguente.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Per creare le funzioni GetCustomers e GetOrders nel servizio dati

1.  Nel **DataService** progetto, fare doppio clic su IService1. vb o IService1.cs.

2.  Aggiungere il codice seguente sotto il **aggiungere qui le operazioni del servizio** commento:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3.  Nel progetto DataService fare doppio clic su Service1.vb o Service1.cs.

4.  Aggiungere il codice seguente alla classe Service1:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5.  Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Creazione di un livello di presentazione per visualizzare i dati dal servizio dati
 Ora che la soluzione contiene il servizio dati con i metodi che effettuano chiamate nel livello di accesso ai dati, creare un altro progetto che effettuerà le chiamate nel servizio dati e presenterà i dati agli utenti. In questa procedura dettagliata, creare un'applicazione Windows Form; si tratta del livello di presentazione dell'applicazione a più livelli.

#### <a name="to-create-the-presentation-tier-project"></a>Per creare il progetto livello di presentazione

1.  Pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliere **Aggiungi**, **nuovo progetto...** .

2.  Nel **nuovo progetto** la finestra di dialogo, nel riquadro a sinistra, seleziona **Windows Desktop classico**. Nel riquadro centrale, selezionare **App di Windows Form**.

3.  Denominare il progetto **PresentationTier** e fare clic su **OK**.

    Il progetto PresentationTier viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Impostazione del progetto PresentationTier come progetto di avvio
Il progetto PresentationTier come progetto di avvio per la soluzione, verrà impostata perché è l'applicazione client effettivo utilizzato per presentare e interagire con i dati.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Impostazione del nuovo livello del progetto come progetto di avvio

-   In **Esplora**, fare doppio clic su **PresentationTier** e fare clic su **imposta come progetto di avvio**.

## <a name="adding-references-to-the-presentation-tier"></a>Aggiunta di riferimenti al livello di presentazione
 Per accedere ai metodi nel servizio, l'applicazione client PresentationTier richiede un riferimento al servizio dati. È richiesto inoltre un riferimento al dataset per abilitare la condivisione dei tipi da parte del servizio WCF. Se non si abilita la condivisione dei tipi con il servizio dati, il codice aggiunto alla classe DataSet parziale non sarà disponibile per il livello di presentazione. Dal momento che di norma si aggiunge codice, ad esempio il codice per la convalida, agli eventi di modifica di righe e colonne di una tabella dati, probabilmente sarà necessario accedere al codice dal client.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Per aggiungere un riferimento al livello di presentazione

1.  In **Esplora**, fare doppio clic su PresentationTier e scegliere **Aggiungi riferimento**.

2.  Nel **Aggiungi riferimento** la finestra di dialogo, seleziona il **progetti** scheda.

3.  Selezionare **DataEntityTier** e scegliere **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Per aggiungere il riferimento a un servizio al livello di presentazione

1.  In **Esplora**, fare doppio clic su PresentationTier e scegliere **Aggiungi riferimento al servizio**.

2.  Nel **Aggiungi riferimento al servizio** nella finestra di dialogo **Discover**.

3.  Selezionare **Service1** e scegliere **OK**.

    > [!NOTE]
    >  Se sono presenti più servizi nel computer in uso, selezionare il servizio creato in precedenza in questa procedura dettagliata, ossia quello contenente i metodi GetCustomers e GetOrders.

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Aggiunta di DataGridView al form per visualizzare i dati restituiti dal servizio dati
 Dopo aver aggiunto il riferimento al servizio al servizio dati, il **origini dati** finestra viene popolata automaticamente con i dati restituiti dal servizio.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Per aggiungere due DataGridView associati a dati al form

1.  In **Esplora**, selezionare il progetto PresentationTier.

2.  Nel **origini dati** finestra, espandere **NorthwindDataSet** e individuare il **clienti** nodo.

3.  Trascinare il **clienti** nodo in Form1.

4.  Nel **origini dati** finestra, espandere il **clienti** nodo e individuare correlata **ordini** nodo (il **ordini** nidificato nel  **I clienti** nodo).

5.  Trascinare correlata **ordini** nodo in Form1.

6.  Fare doppio clic su un'area vuota del form per creare un gestore eventi `Form1_Load`.

7.  Aggiungere il codice seguente al gestore eventi `Form1_Load`.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Aumento della dimensione massima dei messaggi consentita dal servizio
Il valore predefinito per maxReceivedMessageSize non è sufficientemente grande da contenere i dati recuperati dalle tabelle Customers e Orders. Nei passaggi seguenti, si aumenta il valore su 6553600. Si modificherà il valore nel client, che aggiorna automaticamente il riferimento al servizio.

> [!NOTE]
>  La dimensione predefinita più bassa è usata per limitare l'esposizione ad attacchi Denial of Service (DoS). Per altre informazioni, vedere <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Per aumentare il valore di maxReceivedMessageSize

1.  In **Esplora**, fare doppio clic sul file app. config nel progetto PresentationTier.

2.  Individuare il **maxReceivedMessage** attributo di dimensione e impostare il valore su `6553600`.

## <a name="testing-the-application"></a>Verifica dell'applicazione
Eseguire l'applicazione premendo **F5**. I dati delle tabelle Customers e Orders vengono recuperati dal servizio dati e visualizzati nel form.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo il salvataggio dei dati correlati nell'applicazione basata su Windows. È possibile ad esempio apportare i seguenti miglioramenti a questa applicazione:

-   Aggiungere la convalida al dataset.

-   Aggiungere al servizio altri metodi per l'aggiornamento dei dati nel database.

## <a name="see-also"></a>Vedere anche

- [Uso dei set di dati nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)