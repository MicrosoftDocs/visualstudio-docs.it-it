---
title: Creare un'applicazione dati semplice con WPF e di Entity Framework 6 | Documenti Microsoft
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 394dbf9aba422f8fbf16857d6980a53b353e931a
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Creare un'applicazione dati semplice con WPF e di Entity Framework 6

Questa procedura dettagliata viene illustrato come creare un'applicazione di base "form su dati" in Visual Studio con LocalDB di SQL Server, il database Northwind, Entity Framework 6 e Windows Presentation Foundation. Viene illustrato come eseguire l'associazione dati di base con una visualizzazione master-Details e include anche un personalizzati "associazione Navigatore" con i pulsanti "Sposta avanti", "Move Previous," "Sposta all'inizio," "Sposta alla fine," "Aggiorna" e "Delete".  
  
 In questo articolo è incentrato sull'utilizzo degli strumenti di dati in Visual Studio e non tenta di spiegare le tecnologie sottostanti in qualsiasi livello di nidificazione. Si presuppone che si disponga di una conoscenza di base con SQL, Entity Framework e XAML. In questo esempio non viene inoltre architettura Model-View-View MVVM (Model), ovvero standard per le applicazioni WPF. Tuttavia, è possibile copiare questo codice nell'applicazione MVVM con poche modifiche.  
  
## <a name="install-and-connect-to-northwind"></a>Installare e connettersi a Northwind

Questo esempio viene utilizzato SQL Server Express LocalDB e database di esempio Northwind. Dovrebbe funzionare con altri prodotti del database SQL, anche se il provider di dati ADO.NET per il prodotto supporta Entity Framework.  

1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **lo sviluppo desktop .NET** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:  

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .  

       Verrà visualizzata una finestra dell'editor di query.  

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.  

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.  

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.  
  
3.  [Aggiungere nuove connessioni](../data-tools/add-new-connections.md) per Northwind.  
  
## <a name="configure-the-project"></a>Configurare il progetto
  
1.  In Visual Studio, scegliere **File**, **New**, **progetto...**  e quindi creare una nuova applicazione WPF in c#.  
  
2.  Successivamente sarà necessario aggiungere il pacchetto NuGet per Entity Framework 6. In Esplora soluzioni selezionare il nodo del progetto. Nel menu principale scegliere **progetto**, **Gestisci pacchetti NuGet...**  
  
     ![Gestire la voce di menu pacchetti NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  In Gestione pacchetti NuGet, fare clic su di **Sfoglia** collegamento. Entity Framework è probabile che il pacchetto nell'elenco superiore. Fare clic su **installare** nel riquadro di destra e seguire le istruzioni. La finestra di Output indicherà al termine dell'installazione.  
  
     ![Pacchetto NuGet di Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png "raddata_vs2015_Nuget_EF")  
  
4.  È ora possibile usare Visual Studio per creare un modello basato sul database Northwind.  
  
## <a name="create-the-model"></a>Creare il modello
  
1.  Fare clic con il pulsante destro sul nodo del progetto in Esplora soluzioni e scegliere **Aggiungi**, **nuovo elemento...** . Nel riquadro a sinistra, sotto il nodo C#, scegliere **dati** e nel riquadro centrale scegliere **ADO.NET Entity Data Model**.  
  
     ![Entity Framework modello nuovo elemento di progetto](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nuovo elemento di progetto")  

  2.  Chiamare il modello `Northwind_model` e scegliere OK. Verrà visualizzata la **procedura guidata Entity Data Model**. Scegliere **Entity Framework Designer da database** e quindi fare clic su **Avanti**.  
  
     ![Modello EF da Database](../data-tools/media/raddata-ef-model-from-database.png "raddata modello EF da Database")  
  
3.  Nella schermata successiva, scegliere il LocalDB Northwind connessione fare clic su **Avanti**.  
  
4.  Nella pagina successiva della procedura guidata, si sceglie quali tabelle, stored procedure e altri oggetti di database da includere nel modello di Entity Framework. Espandere il nodo dbo nella visualizzazione albero e scegliere i clienti, ordini e dettagli dell'ordine. Lasciare le impostazioni predefinite selezionate e fare clic su **fine**.  
  
     ![Seleziona oggetti di database per il modello](../data-tools/media/raddata-choose-ef-objects.png "raddata Seleziona oggetti di Entity Framework")  
  
5.  La procedura guidata genera le classi c# che rappresentano il modello di Entity Framework. Questi sono normale precedente in c# le classi e si verrà databind all'interfaccia utente WPF. Il file con estensione edmx descrive le relazioni e altri metadati che associa le classi di oggetti nel database.  I file con estensione tt sono modelli T4 che generano il codice che operano sul modello e salvare le modifiche al database. È possibile visualizzare tutti questi file in Esplora soluzioni sotto il nodo Northwind_model:  

       ![File della soluzione EF Esplora modello](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata i file del modello Entity Framework di Esplora soluzioni")  
  
     Area di progettazione per il file con estensione edmx consente di modificare alcune proprietà e relazioni nel modello. Non verrà come utilizzare la finestra di progettazione in questa procedura dettagliata.  
  
6.  I file con estensione tt sono generici, ed è necessario modificare uno di essi per funzionare con l'associazione dati WPF, che richiede ObservableCollections.  In Esplora soluzioni, espandere il nodo Northwind_model finché non si trova Northwind_model.tt. (Assicurarsi che si stia **non** nel *. Contesto file con estensione tt che si trova direttamente sotto il file con estensione edmx).  
  
    -   Sostituire le due occorrenze di <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
    -   Sostituire la prima occorrenza di <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> alla riga 51. Non si sostituisce la seconda occorrenza di HashSet  
  
    -   Sostituire l'unica occorrenza di <xref:System.Collections.Generic> (attorno alla riga 431) con <xref:System.Collections.ObjectModel>.  
  
7.  Premere **Ctrl + MAIUSC + B** per compilare il progetto. Al termine della compilazione, le classi di modello sono visibili per la creazione guidata origine dati.  
  
Ora si è pronti per collegare questo modello nella pagina XAML in modo che possa visualizzare, esplorare e modificare i dati.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Il modello nella pagina XAML DataBind

È possibile scrivere il proprio codice di associazione dati, ma è molto più semplice consentire a Visual Studio permette di.  
  
1.  Dal menu principale scegliere **progetto > Aggiungi nuova origine dati** per visualizzare il **configurazione guidata origine dati**. Scegliere **oggetto** perché viene eseguita l'associazione per le classi di modello, non al database:  
  
     ![Configurazione guidata origine dati con l'oggetto origine](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata configurazione guidata origine dati con l'oggetto origine")  
  
2.  Selezionare cliente.  (Origini per gli ordini verranno automaticamente generate dalla proprietà di navigazione degli ordini cliente.)  
  
     ![Aggiungere le classi di entità come origini dati](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Aggiungi entità classi come origini dati")  
  
3.  Fare clic su **fine**  
  
4.  Passare a MainWindow. XAML nella visualizzazione codice. Verrà per mantenere il codice XAML molto semplice per fini di questo esempio. Modificare il titolo della finestra principale per renderlo più descrittivo e aumentare l'altezza e larghezza di 600 x 800 per ora. È possibile sempre modificarlo in un secondo momento. Aggiungi ora le definizioni di tre righe alla griglia principale, una riga per i pulsanti di navigazione, uno per i dettagli del cliente, uno per la griglia in cui viene ordini:  

    ```xaml  
    <Grid.RowDefinitions>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="*"/>  
        </Grid.RowDefinitions>
    ```

5.  Ora aprire MainWindow. XAML in modo che venga visualizzato nella finestra di progettazione. In questo modo, la finestra Origini dati vengono visualizzati come un'opzione nel margine accanto della casella degli strumenti finestra Visual Studio. Fare clic sulla scheda per aprire la finestra o in caso contrario premere **Maiusc + Alt + D** oppure scegliere **View &#124; Altri Windows &#124; Origini dati**. Verranno visualizzare ogni proprietà della classe di clienti nella propria casella di testo. Prima di fare clic sulla freccia nella casella combinata dei clienti e scegliere **dettagli**. Trascinare quindi il nodo nella parte centrale dell'area di progettazione, in modo che la finestra di progettazione sia in grado che si desidera venga inserito nella riga centrale.  Se si sono disponibili, è possibile specificare la riga manualmente in un secondo momento nel codice XAML. Per impostazione predefinita, i controlli vengono posizionati verticalmente in un elemento della griglia, ma a questo punto è possibile disporle nel modo desiderato nel form.  Ad esempio, potrebbe essere opportuno inserire una casella di testo nome nella parte superiore, sopra l'indirizzo. L'applicazione di esempio per l'articolo riordina i campi e consente di riorganizzare in due colonne.  
  
     ![Associazione dell'origine dati i clienti ai singoli controlli](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "associazione all'origine dati clienti raddata sui singoli controlli")  
  
     Nella visualizzazione codice, è ora possibile visualizzare un nuovo `Grid` nella riga 1 (la riga centrale) dell'elemento padre della griglia. L'elemento padre della griglia è un `DataContext` attributo che fa riferimento a CollectionViewSource che è stato aggiunto il `Windows.Resources` elemento. Dato il contesto dei dati, quando la prima casella di testo, ad esempio, viene associato a tale nome "Address" viene mappato al `Address` proprietà nell'oggetto `Customer` oggetto CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  

6.  Quando un cliente è visibile nella parte superiore della finestra, si desidera visualizzare gli ordini nella parte inferiore a metà. Vi mostreremo gli ordini in un controllo di visualizzazione griglia singolo. Per l'associazione dati master-details funzionare come previsto, è importante che l'associazione alla proprietà ordini nella classe di clienti, non per il nodo Orders separato. Prestare attenzione alla figura riportata di seguito. Trascinare la proprietà di ordini della classe di clienti nella metà inferiore del form, in modo che la finestra di progettazione lo inserisce nella riga 2:  
  
     ![Trascinare le classi di ordini come griglia](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata Trascinare Orders classi come griglia")  
  
7.  Tutto il codice di associazione che si connette a controlli dell'interfaccia utente per gli eventi del modello è generata da Visual Studio. È necessario eseguire, per visualizzare alcuni dati, è sufficiente scrivere del codice per popolare il modello. Primo consente di passare alla MainWindow.xaml.cs e aggiungere un membro dati classe MainWindow per il contesto dei dati. Questo oggetto, che è stato generato automaticamente, svolge la funzione simile a un controllo che tiene traccia delle modifiche e gli eventi del modello. Viene inoltre aggiunta la logica di inizializzazione del costruttore. La parte superiore della classe dovrebbe essere simile al seguente:  
  
     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]  
     
     Aggiungere un `using` direttiva System.Data.Entity portare il metodo di estensione carico nell'ambito:  
  
     ```csharp
     using System.Data.Entity;  
     ```  

     A questo punto, scorrere verso il basso e trovare il gestore dell'evento Window_Loaded. Si noti che Visual Studio ha aggiunto un oggetto CollectionViewSource per noi. Questo rappresenta l'oggetto NorthwindEntities è selezionata, quando abbiamo creato il modello. Aggiungere codice a Window_Loaded in modo che l'intero metodo ora simile al seguente:  

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]  

8.  Premere **F5**. È necessario visualizzare i dettagli per il primo cliente che è stato recuperato in CollectionViewSource. Verrà visualizzato anche i relativi ordini nella griglia dei dati. La formattazione non è grande, a questo punto che Correggi. Si creerà anche un modo per visualizzare gli altri record ed eseguire operazioni CRUD di base.  

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Modificare la struttura della pagina e aggiungere le griglie per nuovi clienti e ordini

La disposizione predefinito generata da Visual Studio non è ideale per l'applicazione, in modo da apportare alcune modifiche manualmente nel codice XAML. Alcuni "Form", che sono effettivamente griglie, è necessario anche per consentire all'utente di aggiungere un nuovo cliente o un ordine. Per poter aggiungere un nuovo cliente e ordine, è necessario un set separato di caselle di testo che non sono associati a dati per il `CollectionViewSource`. Si sarà controllare quali griglia viene visualizzata in qualsiasi momento impostando la proprietà Visible nei metodi del gestore. Infine, si aggiungerà un pulsante Elimina a ogni riga nella griglia gli ordini per consentire all'utente di eliminare un singolo ordine.  
  
In primo luogo, è possibile aggiungere questi stili all'elemento Windows.Resources in MainWindow. XAML:  
  
```xaml  
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Left"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="23"/>  
</Style>  
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Right"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="26"/>  
    <Setter Property="Width" Value="120"/>  
</Style>  
```  
  
Successivamente, sostituire l'intera griglia esterno con questo codice:  
  
```xaml  
<Grid>  
     <Grid.RowDefinitions>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="*"/>  
     </Grid.RowDefinitions>   
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="New Order Form" FontWeight="Bold"/>  
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"  
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">  
         <DataGrid.Columns>  
             <DataGridTemplateColumn>  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>  
         </DataGrid.Columns>  
     </DataGrid>  
 </Grid>  
```  
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Aggiungere pulsanti per spostarsi, aggiungere, aggiornare ed eliminare  

Nelle applicazioni Windows Form, ottenere un oggetto di BindingNavigator con pulsanti per spostarsi tra le righe in un database e l'esecuzione di operazioni CRUD di base. WPF non fornisce un controllo BindingNavigator, ma è sufficiente crearne uno. Che verranno eseguite con i pulsanti all'interno di un elemento StackPanel orizzontale e sarà Associamo i pulsanti con i comandi che verranno associati ai metodi nel code-behind.  
  
Esistono quattro parti per la logica di comando: (1) i comandi, (2) le associazioni, (3) i pulsanti e (4) i gestori di comando nel code-behind.  
  
### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Aggiungere i comandi, associazioni e i pulsanti in XAML
  
1.  In primo luogo, aggiungere i comandi nel file MainWindow. XAML all'interno dell'elemento Windows.Resources:  
  
    ```xaml  
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>  
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>  
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>  
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>  
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>  
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>  
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>  
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>  
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>  
    ```  
  
2.  Un oggetto CommandBinding esegue il mapping di un evento RoutedUICommand a un metodo nel code-behind. Aggiungere questo elemento CommandBindings dopo il tag di chiusura di Windows.Resources:  
  
    ```xaml  
    <Window.CommandBindings>  
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>  
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>  
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>  
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>  
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>  
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>  
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>  
    </Window.CommandBindings>  
    ```  
  
3.  Ora si aggiungere StackPanel con la navigazione, aggiungere, eliminare e aggiornare i pulsanti. In primo luogo, aggiungere questo stile Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     In secondo luogo, è possibile incollare questo codice subito dopo il RowDefinitions per l'elemento griglia esterno, nella parte superiore della pagina XAML:  
  
    ```xaml  
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
    </StackPanel>  
    ```  
  
### <a name="add-command-handlers-to-the-mainwindow-class"></a>Aggiungere gestori di comandi alla classe MainWindow  
  
Il code-behind è minimo ad eccezione dei metodi di aggiunta ed eliminazione. Navigazione viene eseguita chiamando metodi sulla proprietà di visualizzazione di CollectionViewSource. Il DeleteOrderCommandHandler viene illustrato come eseguire un'eliminazione a catena in un ordine. È necessario innanzitutto eliminare Order_Details che esso associati. Il UpdateCommandHandler aggiunge un nuovo cliente o un ordine alla raccolta, altrimenti aggiorni un cliente esistente o un ordine con le modifiche apportate dall'utente nelle caselle di testo.  
  
Aggiungere questi metodi del gestore della classe MainWindow in MainWindow.xaml.cs. Se l'oggetto CollectionViewSource per la tabella Customers è un nome diverso, è necessario modificare il nome in ognuno di questi metodi:  
  
[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]  
  
## <a name="run-the-application"></a>Esecuzione dell'applicazione

Premere **F5** per avviare il debug. Si dovrebbe essere dati del cliente e ordine popolati nella griglia e i pulsanti di navigazione devono funzionare come previsto. Fare clic su "Commit" per aggiungere un nuovo cliente o un ordine per il modello dopo aver immesso i dati. Fare clic su "Annulla" per eseguire il backup da un nuovo cliente o un nuovo modulo d'ordine senza salvare i dati. È possibile apportare modifiche agli ordini direttamente nelle caselle di testo e i clienti esistenti e tali modifiche vengono scritte automaticamente il modello.  
  
## <a name="see-also"></a>Vedere anche

[Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)  
[Documentazione di Entity Framework](/ef/)