---
title: 'Procedura dettagliata: Creazione di un servizio dati WCF con WPF e di Entity Framework | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c4db93f300c47bf3a09dac2fbf9d5b1f4bc17108
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Procedura dettagliata: Creazione di un servizio dati WCF con WPF e di Entity Framework
Questa procedura dettagliata viene illustrato come creare un semplice [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] che è ospitato in un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione Web e quindi accedervi da un'applicazione Windows Form.  
  
In questa procedura dettagliata vengono illustrate le seguenti operazioni:  
  
-   Creare un'applicazione Web per ospitare un servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Creazione di un modello [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] che rappresenta la tabella Customers nel database Northwind.  
  
-   Creare un oggetto [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Creare un'applicazione client e aggiungere un riferimento al servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Abilitazione del data binding al servizio e generazione dell'interfaccia utente.  
  
-   Aggiunta facoltativa di funzionalità di filtraggio all'applicazione.  
  
## <a name="prerequisites"></a>Prerequisiti  
Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.  
  
1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.  
  
2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:  

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .  

       Verrà visualizzata una finestra dell'editor di query.  

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.  

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.  

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.  
  
## <a name="creating-the-service"></a>Creazione del servizio  
Per creare un servizio [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], è necessario aggiungere un progetto Web, creare un modello [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], quindi creare il servizio dal modello.  
  
Nel primo passaggio, verrà aggiunto un progetto Web in cui includere il servizio.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-the-web-project"></a>Per creare il progetto Web  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual Basic** o **Visual c#** e **Web** nodi, quindi scegliere il **ASP. Applicazione Web NET** modello.  
  
3.  Nel **nome** testo immettere **NorthwindWeb**, quindi scegliere il **OK** pulsante.  
  
4.  Nel **nuovo progetto ASP.NET** della finestra di dialogo di **selezionare un modello** scegliere **vuoto**e quindi scegliere il **OK** pulsante.  
  
Nel passaggio successivo, si creerà un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] che rappresenta la tabella Customers nel database Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Per creare il modello Entity Data Model  
  
1.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere il **dati** nodo, quindi scegliere il **ADO.NET Entity Data Model** elemento.  
  
3.  Nel **nome** testo immettere `NorthwindModel`, quindi scegliere il **Aggiungi** pulsante.  
  
     Verrà visualizzata la procedura guidata Entity Data Model.  
  
4.  Nella procedura guidata Entity Data Model, nel **Scegli contenuto Model** pagina, scegliere il **Entity Framework Designer da database** elemento e quindi scegliere il **Avanti** pulsante.  
  
5.  Nella pagina **Seleziona connessione dati** , eseguire una delle operazioni seguenti:  
  
    -   Nell'elenco a discesa scegliere una connessione dati al database di esempio Northwind, se disponibile.  
  
         oppure  
  
    -   Scegliere il **nuova connessione** pulsante per configurare una nuova connessione dati. Per ulteriori informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).  
  
6.  Se il database richiede una password, scegliere il **Sì, Includi i dati sensibili nella stringa di connessione** pulsante di opzione e quindi scegliere il **Avanti** pulsante.  
  
    > [!NOTE]
    >  Se viene visualizzata una finestra di dialogo, scegliere **Sì** per salvare il file al progetto.  
  
7.  Nel **scegliere la versione** pagina, scegliere il **Entity Framework 5.0** pulsante di opzione e quindi scegliere il **Avanti** pulsante.  
  
    > [!NOTE]
    >  Per utilizzare la versione più recente di Entity Framework 6 con i servizi WCF, è necessario installare il pacchetto NuGet WCF Data Services Entity Framework Provider. Vedere [tramite WCF Data Services 5.6.0 with Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8.  Nel **Seleziona oggetti di Database** espandere la **tabelle** nodo, seleziona il **clienti** casella di controllo e quindi scegliere il **fine** pulsante.  
  
     Viene visualizzato il diagramma del modello di entità e viene aggiunto un file NorthwindModel.edmx al progetto.  
  
Nel passaggio successivo, verranno creare e testare il servizio dati.  
  
#### <a name="to-create-the-data-service"></a>Per creare il servizio dati  
  
1.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere il **Web** nodo, quindi scegliere il **WCF Data Service 5.6** elemento.  
  
3.  Nel **nome** testo immettere `NorthwindCustomers`, quindi scegliere il **Aggiungi** pulsante.  
  
     Il file NorthwindCustomers.svc verrà visualizzato nel **Editor di codice**.  
  
4.  Nel **Editor di codice**, individuare il primo `TODO:` impostare come commento e sostituire il codice con quanto segue:  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  Sostituire i commenti nel gestore eventi `InitializeService` con il codice seguente:  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  Nella barra dei menu, scegliere **Debug**, **Avvia senza eseguire debug** per eseguire il servizio. Verrà aperta una finestra del browser nella quale sarà visualizzato l'XML Schema per il servizio.  
  
7.  Nel **indirizzo** barra, immettere `Customers` alla fine dell'URL per NorthwindCustomers.svc, quindi scegliere il **invio** chiave.  
  
     Verrà visualizzata una rappresentazione XML dei dati della tabella Customers.  
  
    > [!NOTE]
    >  In alcuni casi, Internet Explorer interpreterà erroneamente i dati come feed RSS. È necessario assicurarsi che l'opzione per visualizzare feed RSS sia disabilitata. Per ulteriori informazioni, vedere [riferimenti al servizio di risoluzione dei problemi](../data-tools/troubleshooting-service-references.md).  
  
8.  Chiudere la finestra del browser.  
  
Nei passaggi successivi, verrà creata un'applicazione client Windows Form che consente di usare il servizio.  
  
## <a name="creating-the-client-application"></a>Creazione dell'applicazione client  
 Per creare l'applicazione client, sarà necessario aggiungere un secondo progetto, aggiungere un riferimento al servizio per il progetto, configurare un'origine dati e creare un'interfaccia utente per visualizzare i dati del servizio.  
  
 Nel primo passaggio, alla soluzione verrà aggiunto un progetto Windows Form che sarà impostato come progetto di avvio.  
  
#### <a name="to-create-the-client-application"></a>Per creare l'applicazione client  
  
1.  Nella barra dei menu scegliere File, **Aggiungi**, **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual Basic** o **Visual c#** nodo e scegliere il **Windows** nodo, quindi scegliere  **Applicazione Windows Form**.  
  
3.  Nella casella di testo **Nome** immettere `NorthwindClient` e quindi scegliere il pulsante **OK**.  
  
4.  In **Esplora**, scegliere il **NorthwindClient** nodo del progetto.  
  
5.  Nella barra dei menu, scegliere **progetto**, **imposta come progetto di avvio**.  
  
Nel passaggio successivo, si aggiungerà un riferimento al servizio di [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] nel progetto Web.  
  
#### <a name="to-add-a-service-reference"></a>Per aggiungere un riferimento al servizio  
  
1.  Nella barra dei menu, scegliere **progetto**, **Aggiungi riferimento al servizio**.  
  
2.  Nel **Aggiungi riferimento al servizio** finestra di dialogo scegliere la **Discover** pulsante.  
  
     L'URL per il servizio NorthwindCustomers verrà visualizzato il **indirizzo** campo.  
  
3.  Scegliere il **OK** pulsante per aggiungere il riferimento al servizio.  
  
Nel passaggio successivo si configurerà un'origine dati per consentire il data binding al servizio.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Per abilitare il data binding al servizio  
  
1.  Nella barra dei menu, scegliere **vista**, **altre finestre**, **origini dati**.  
  
2.  Nel **origini dati** finestra, scegliere il **Aggiungi nuova origine dati** pulsante.  
  
3.  Nel **scegliere un tipo di origine dati** pagina del **configurazione guidata origine dati**, scegliere **oggetto**e quindi scegliere il **Avanti** pulsante .  
  
4.  Nel **selezionare gli oggetti dati** espandere il **NorthwindClient** nodo, quindi espandere il **NorthwindClient.ServiceReference1** nodo.  
  
5.  Selezionare **cliente** casella di controllo e quindi scegliere il **fine** pulsante.  
  
Nel passaggio successivo, si creerà l'interfaccia utente che consente di visualizzare i dati dal servizio.  
  
#### <a name="to-create-the-user-interface"></a>Per creare l'interfaccia utente  
  
1.  Nel **origini dati** finestra, aprire il menu di scelta rapida per il **clienti** nodo e scegliere **copia**.  
  
2.  Nel **Form1. vb** o **Form1. cs** progettazione form, aprire il menu di scelta rapida e scegliere **Incolla**.  
  
     Al form vengono aggiunti un controllo <xref:System.Windows.Forms.DataGridView>, un componente <xref:System.Windows.Forms.BindingSource> e un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
3.  Scegliere il **CustomersDataGridView** (controllo) e quindi il **proprietà** finestra set il **Dock** proprietà **riempimento**.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il **Form1** nodo e scegliere **Visualizza codice** per aprire l'Editor di codice e aggiungere i seguenti riferimenti importati o istruzione nel inizio del file:  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```csharp  
    using NorthwindClient.ServiceReference1;  
    ```  
  
5.  Aggiungere il codice seguente al gestore eventi `Form1_Load`:  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
            Dim proxy As New NorthwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
            Me.CustomersBindingSource.DataSource = proxy.Customers  
        End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  In **Esplora**, aprire il menu di scelta rapida per il file NorthwindCustomers.svc e scegliere **Visualizza nel Browser**. Verrà aperto Internet Explorer e verrà visualizzato l'XML Schema per il servizio.  
  
7.  Copiare l'URL dalla barra degli indirizzi di Internet Explorer.  
  
8.  Nel codice aggiunto nel passaggio 4, selezionare `http://localhost:53161/NorthwindCustomers.svc/` e sostituirlo con l'URL appena copiato.  
  
9. Nella barra dei menu, scegliere **Debug**, **Avvia debug** per eseguire l'applicazione. Verranno visualizzate le informazioni sul cliente.  
  
 A questo punto si disporrà di un'applicazione nella quale sarà visualizzato un elenco di clienti del servizio NorthwindCustomers. Se si desidera esporre altri dati tramite il servizio, è possibile modificare [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] per includere tabelle aggiuntive dal database Northwind.  
  
Nel prossimo passaggio facoltativo, verrà illustrato come filtrare i dati restituiti dal servizio.  
  
## <a name="adding-filtering-capabilities"></a>Aggiunta di funzionalità di filtraggio  
 In questo passaggio, verrà personalizzata l'applicazione per filtrare i dati in base alla città del cliente.  
  
#### <a name="to-add-filtering-by-city"></a>Per aggiungere il filtraggio in base alla città  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **Form1. vb** o **Form1. cs** nodo e scegliere **aprire**.  
  
2.  Aggiungere un <xref:System.Windows.Forms.TextBox> controllo e un <xref:System.Windows.Forms.Button> controllo il **della casella degli strumenti** al form.  
  
3.  Aprire il menu di scelta rapida per il <xref:System.Windows.Forms.Button> controllo e scegliere **Visualizza codice**, quindi aggiungere il codice seguente nel `Button1_Click` gestore eventi:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```csharp  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  Nel codice precedente, sostituire `http://localhost:53161/NorthwindCustomers.svc` con l'URL del gestore eventi `Form1_Load`.  
  
5.  Nella barra dei menu, scegliere **Debug**, **Avvia debug** per eseguire l'applicazione.  
  
6.  Nella casella di testo immettere **Londra**e quindi scegliere il pulsante. Verranno visualizzati solo i clienti di Londra.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)