---
title: "Salvare i dati in un database (a più tabelle) | Documenti Microsoft"
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e3841a0052081700be899576e1adc0a0740fecec
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvare i dati in un database (a più tabelle)
Uno degli scenari più comuni nello sviluppo di applicazioni è la visualizzazione di dati in un form in un'applicazione Windows, la modifica dei dati e l'invio dei dati aggiornati al database. In questa procedura dettagliata viene creato un form in cui sono visualizzati i dati di due tabelle correlate e viene illustrato come modificare i record e salvare le modifiche nel database. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
 È possibile salvare nel database i dati dell'applicazione chiamando il metodo `Update` di un oggetto TableAdapter. Quando si trascinano tabelle dal **origini dati** finestra in un form, il codice che ha richiesto di salvare i dati viene aggiunto automaticamente. Le tabelle aggiuntive che vengono aggiunti a un form richiedono l'aggiunta manuale del codice. In questa procedura dettagliata viene descritto come aggiungere il codice per salvare gli aggiornamenti da più di una tabella.  
  
> [!NOTE]
>  Finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo **Windows Forms Application** progetto.  
  
-   Creazione e configurazione di un'origine dati nell'applicazione con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Impostazione dei controlli degli elementi di [finestra Origini dati](add-new-data-sources.md). Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione di controlli con associazione a dati trascinando elementi dal **origini dati** finestra nel form.  
  
-   La modifica di alcuni record in ogni tabella nel set di dati.  
  
-   Modifica del codice per inviare nuovamente al database i dati aggiornati nel set di dati.  
  
## <a name="prerequisites"></a>Prerequisiti  
Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.  
  
1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.  
  
2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:  

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .  

       Verrà visualizzata una finestra dell'editor di query.  

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.  

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.  

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.  
  
## <a name="create-the-windows-forms-application"></a>Creare l'applicazione Windows Form  
 Il primo passaggio consiste nel creare un **applicazione Windows Form**. Assegnazione di un nome per il progetto è facoltativo durante questo passaggio, ma è possibile assegnargli un nome perché è possibile risparmiare il progetto in un secondo momento.  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>Per creare il nuovo progetto di applicazione Windows Form  
  
1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .  
  
2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.  

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.  

4. Denominare il progetto **UpdateMultipleTablesWalkthrough**, quindi scegliere **OK**. 
  
     Il **UpdateMultipleTablesWalkthrough** progetto viene creato e aggiunto a **Esplora**.  
  
## <a name="create-the-data-source"></a>Creare l'origine dati  
 Questo passaggio verrà creata un'origine dati dal database Northwind usando la **configurazione guidata origine dati**. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sull'impostazione di database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Nel **dati** dal menu **Mostra origini dati**.  
  
2.  Nel **origini dati** selezionare**Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati**.  
  
3.  Nel **scegliere un tipo di origine dati** selezionare **Database**, quindi selezionare **Avanti**.  
  
4.  Nel **Seleziona connessione dati** eseguire schermata una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         oppure  
  
    -   Selezionare **nuova connessione** per aprire la **Aggiungi/Modifica connessione** la finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati riservati, quindi selezionare **Avanti**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione**selezionare **Avanti**.  
  
7.  Nel **Seleziona oggetti di Database**schermata, quindi espandere il **tabelle** nodo.  
  
8.  Selezionare il **clienti** e **ordini** tabelle e quindi selezionare **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e le tabelle vengono visualizzate nel **origini dati** finestra.  
  
## <a name="set-the-controls-to-be-created"></a>Impostare i controlli da creare  
 Per questa procedura dettagliata, i dati di `Customers` la tabella è in un **dettagli** layout in cui i dati vengono visualizzati in singoli controlli. I dati dal `Orders` tabella è presente un **griglia** layout che viene visualizzato in un <xref:System.Windows.Forms.DataGridView> controllo.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Per impostare il tipo di rilascio degli elementi della finestra Origini dati  
  
1.  Nel **origini dati** finestra, espandere il **clienti** nodo.  
  
2.  Nel **clienti** nodo, seleziona **dettagli** dall'elenco di controllo per impostare il controllo del **clienti** tabella sui singoli controlli. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Creare il form con associazione a dati  
 È possibile creare i controlli con associazione a dati trascinando elementi dal **origini dati** finestra nel form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form  
  
1.  Trascinare principale **clienti** nodo dal **origini dati** finestra **Form1**.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
2.  Trascinare correlata **ordini** nodo dal **origini dati** finestra **Form1**.  
  
    > [!NOTE]
    >  Correlata **ordini** nodo si trova sotto il **Fax** colonna ed è un nodo figlio del **clienti** nodo.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Un `OrdersTableAdapter` e <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.  
  
## <a name="add-code-to-update-the-database"></a>Aggiungere il codice per aggiornare il database  
 È possibile aggiornare il database chiamando il `Update` metodi del **clienti** e **ordini** oggetti TableAdapter. Per impostazione predefinita, un gestore eventi per il **salvare** pulsante il<xref:System.Windows.Forms.BindingNavigator> viene aggiunto al codice del form per inviare aggiornamenti al database. Questa procedura consente di modificare il codice per inviare gli aggiornamenti nell'ordine corretto. In questo modo si elimina la possibilità di errori di integrità referenziale. Il codice implementa anche la gestione degli errori eseguendo il wrapping della chiamata di aggiornamento in un blocco try-catch. È possibile modificare il codice per soddisfare le esigenze dell'applicazione.  
  
> [!NOTE]
>  Per maggiore chiarezza, questa procedura dettagliata non utilizza una transazione. Tuttavia, se si sta aggiornando due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione. Una transazione è un processo che assicura che tutte le modifiche relative a un database vengano completate prima di tutte le modifiche vanno eseguito il commit. Per ulteriori informazioni, vedere [transazioni e concorrenza](/dotnet/framework/data/adonet/transactions-and-concurrency).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Per aggiungere la logica di aggiornamento all'applicazione  
  
1.  Selezionare il **salvare** pulsante il <xref:System.Windows.Forms.BindingNavigator>. Si aprirà l'Editor di codice per il `bindingNavigatorSaveItem_Click` gestore dell'evento.  
  
2.  Sostituire il codice nel gestore eventi per chiamare i metodi `Update` degli oggetti TableAdapter correlati. Il codice seguente crea innanzitutto tre tabelle dati temporanee in cui inserire le informazioni aggiornate per ogni <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> e <xref:System.Data.DataRowState.Modified>). Gli aggiornamenti vengono quindi eseguiti nell'ordine corretto. Il codice dovrebbe essere simile al seguente:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Selezionare **F5**.  
  
2.  Apportare alcune modifiche ai dati di uno o più record di ogni tabella.  
  
3.  Selezionare il **salvare** pulsante.  
  
4.  Controllare i valori presenti nel database per verificare che le modifiche siano state salvate.  
  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)