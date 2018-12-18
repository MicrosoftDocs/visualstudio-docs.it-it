---
title: Gestire un'eccezione di concorrenza | Documenti Microsoft
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 71572ac38c7aed3154360d3bad9e4b84fe0107e3
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="handle-a-concurrency-exception"></a>Gestire un'eccezione di concorrenza
Le eccezioni di concorrenza (<xref:System.Data.DBConcurrencyException>) vengono generati quando due utenti tentano di modificare gli stessi dati in un database nello stesso momento. In questa procedura dettagliata, si crea un'applicazione Windows che viene illustrato come intercettare un <xref:System.Data.DBConcurrencyException>, individuare la riga che ha causato l'errore e una strategia per la gestione di informazioni.  
  
 Questa procedura dettagliata descrive come eseguire il processo seguente:  
  
1.  Creare un nuovo progetto di **Applicazione Windows Form**.  
  
2.  Creare un nuovo set di dati basato su Northwind `Customers` tabella.  
  
3.  Creare un form con un <xref:System.Windows.Forms.DataGridView> per visualizzare i dati.  
  
4.  Compilare un set di dati con i dati di `Customers` tabella nel database Northwind.  
  
5.  Utilizzare il **Mostra dati tabella** funzionalità in **Esplora Server** per l'accesso di `Customers` dati e modificare un record della tabella.  
  
6.  Modificare lo stesso record in un valore diverso, aggiornare il set di dati e tentano di scrivere le modifiche al database, che comporta un errore di concorrenza.  
  
7.  Genera l'errore, quindi visualizzare le diverse versioni del record, che consente all'utente di determinare se continuare e aggiornare il database o per annullare l'aggiornamento.  
  
## <a name="prerequisites"></a>Prerequisiti  
Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.  
  
1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.  
  
2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:  

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .  

       Verrà visualizzata una finestra dell'editor di query.  

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.  

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.  

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.  
  
> [!NOTE]
>  Finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Creare un nuovo progetto  
 Iniziare la procedura dettagliata creando una nuova applicazione Windows Form.  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Per creare un nuovo progetto di applicazione Windows Forms  
  
1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .  
  
2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.  

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.  

4. Denominare il progetto **ConcurrencyWalkthrough**, quindi scegliere **OK**. 
  
     Il **ConcurrencyWalkthrough** progetto viene creato e aggiunto a **Esplora**, e viene aperto un nuovo form nella finestra di progettazione.  
  
## <a name="create-the-northwind-dataset"></a>Creare il set di dati di Northwind  
 In questa sezione si crea un set di dati denominato `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>Per creare NorthwindDataSet  
  
1.  Nel **dati** menu, scegliere **origine aggiungere nuovi dati**.  
  
     Il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) apre.  
  
2.  Nel **scegliere un tipo di origine dati** selezionare **Database**.  
  
3.  Selezionare una connessione al database di esempio Northwind nell'elenco delle connessioni disponibili. Se la connessione non è disponibile nell'elenco di connessioni, selezionare **nuova connessione**  
  
    > [!NOTE]
    >  Se ci si connette a un file di database locale, selezionare **n** quando viene chiesto se si desidera aggiungere il file al progetto.  
  
4.  Nel **Salva stringa di connessione al file di configurazione dell'applicazione** selezionare **Avanti**.  
  
5.  Espandere il **tabelle** nodo e selezionare il `Customers` tabella. Il nome predefinito per il set di dati deve essere `NorthwindDataSet`.  
  
6.  Selezionare **fine** per aggiungere il set di dati al progetto.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Creare un controllo DataGridView con associazione a dati  
 In questa sezione si crea un <xref:System.Windows.Forms.DataGridView> trascinando il **clienti** articolo dal **origini dati** finestra sul Windows Form.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Per creare un controllo DataGridView associato alla tabella Customers  
  
1.  Nel **dati** menu, scegliere **Mostra origini dati** per aprire la **finestra Origini dati**.  
  
2.  Nel **origini dati** finestra, espandere il **NorthwindDataSet** nodo e quindi selezionare il **clienti** tabella.  
  
3.  Selezionare la freccia rivolta verso il basso nel nodo della tabella, quindi **DataGridView** nell'elenco a discesa.  
  
4.  Trascinare la tabella in un'area vuota del form.  
  
     A <xref:System.Windows.Forms.DataGridView> controllo denominato `CustomersDataGridView` e <xref:System.Windows.Forms.BindingNavigator> denominato `CustomersBindingNavigator` vengono aggiunti al form a cui è associato il <xref:System.Windows.Forms.BindingSource>. Questa operazione, è in, viene associato che attiva per il `Customers` tabella il `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Verificare il modulo  
 È ora possibile testare il form per assicurarsi che tutto funzioni come previsto fino a questo punto.  
  
#### <a name="to-test-the-form"></a>Per verificare il modulo  
  
1.  Selezionare **F5** per eseguire l'applicazione  
  
     Il form viene visualizzato con un <xref:System.Windows.Forms.DataGridView> controllo che viene riempito con i dati di `Customers` tabella.  
  
2.  Nel **Debug** dal menu **Termina debug**.  
  
## <a name="handle-concurrency-errors"></a>Gestire gli errori di concorrenza  
 Modalità di gestione degli errori varia a seconda di specifiche regole aziendali che regolano l'applicazione. Questa procedura dettagliata, come un esempio di come gestire l'errore di concorrenza viene usata la strategia di seguito.  
  
 L'applicazione presenta all'utente e tre le versioni del record:  
  
-   Il record corrente nel database  
  
-   Il record originale che viene caricato nel set di dati  
  
-   Le modifiche proposte nel set di dati  
  
L'utente sarà in grado di sovrascrivere il database con la versione proposta, o annullare l'aggiornamento e aggiornare il set di dati con i nuovi valori dal database.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Per abilitare la gestione degli errori di concorrenza  
  
1.  Creare un gestore degli errori personalizzati.  
  
2.  Visualizzare le opzioni per l'utente.  
  
3.  Elaborare la risposta dell'utente.  
  
4.  Inviare di nuovo l'aggiornamento o reimpostare i dati nel set di dati.  
  
### <a name="add-code-to-handle-the-concurrency-exception"></a>Aggiungere codice per gestire le eccezioni di concorrenza  
 Quando si tenta di eseguire un aggiornamento e viene generata l'eccezione, in genere da operazioni con le informazioni fornite per l'eccezione generata.  
  
 In questa sezione, aggiungere codice che tenta di aggiornare il database. È anche possibile gestire qualsiasi <xref:System.Data.DBConcurrencyException> generata, così come qualsiasi altra eccezione.  
  
> [!NOTE]
>  Il `CreateMessage` e `ProcessDialogResults` metodi verranno aggiunti più avanti in questa procedura dettagliata.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Per aggiungere la gestione dell'errore di concorrenza  
  
1.  Aggiungere il codice seguente sotto il `Form1_Load` metodo:  
  
     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  Sostituire il `CustomersBindingNavigatorSaveItem_Click` metodo da chiamare il `UpdateDatabase` metodo in modo che rispecchi simile al seguente:  
  
     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### <a name="display-choices-to-the-user"></a>Impostazioni di visualizzazione per l'utente  
 Il codice appena il `CreateMessage` procedura per visualizzare informazioni sull'errore all'utente. Questa procedura dettagliata, è utilizzare una finestra di messaggio per visualizzare le diverse versioni del record per l'utente. Ciò consente all'utente di scegliere se sovrascrivere il record con le modifiche oppure annullare la modifica. Una volta che l'utente seleziona un'opzione (un pulsante) nella finestra di messaggio, la risposta viene passata per il `ProcessDialogResult` metodo.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Per creare il messaggio da visualizzare all'utente  
  
-   Creare il messaggio aggiungendo il codice seguente per il **Editor di codice**. Immettere questo codice sotto il `UpdateDatabase` metodo.  
  
     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### <a name="process-the-users-response"></a>Elaborare la risposta dell'utente  
 È inoltre necessario codice per elaborare la risposta dell'utente per la finestra di messaggio. Le opzioni sono per sovrascrivere il record corrente nel database con la modifica proposta, o ignorare le modifiche locali e aggiornare la tabella di dati con il record che è attualmente nel database. Se l'utente sceglie Sì, il <xref:System.Data.DataTable.Merge%2A> metodo viene chiamato con il *preserveChanges* argomento impostato su `true`. In questo modo il tentativo di aggiornamento abbia esito positivo, perché la versione originale del record corrisponde ora al record nel database.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Per elaborare l'utente di input dalla finestra di messaggio  
  
-   Aggiungere il codice seguente sotto il codice che è stato aggiunto nella sezione precedente.  
  
     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## <a name="test-the-form"></a>Verificare il modulo  
 È ora possibile testare il form per assicurarsi che tutto funzioni come previsto. Per simulare una violazione della concorrenza che è necessario modificare i dati nel database dopo la compilazione di NorthwindDataSet.  
  
#### <a name="to-test-the-form"></a>Per verificare il modulo  
  
1.  Selezionare **F5** per eseguire l'applicazione.  
  
2.  Una volta visualizzato il form, lasciare in esecuzione e passare all'IDE di Visual Studio.  
  
3.  Nel **vista** menu, scegliere **Esplora Server**.  
  
4.  In **Esplora Server**, espandere la connessione utilizzando l'applicazione e quindi espandere il **tabelle** nodo.  
  
5.  Fare doppio clic su di **clienti** tabella e quindi selezionare **Mostra dati tabella**.  
  
6.  Nel primo record (`ALFKI`) modificare `ContactName` a `Maria Anders2`.  
  
    > [!NOTE]
    >  Passare a un'altra riga per eseguire il commit della modifica.  
  
7.  Passare il `ConcurrencyWalkthrough`form in esecuzione.  
  
8.  Nel primo record del form (`ALFKI`), modificare`ContactName` a `Maria Anders1`.  
  
9. Selezionare il **salvare** pulsante.  
  
     Viene generato l'errore di concorrenza e viene visualizzata la finestra di messaggio.  
  
10. Selezione **n** Annulla l'aggiornamento e aggiorna il set di dati con i valori presenti nel database. Selezione **Sì** scrive il valore proposto per il database.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
