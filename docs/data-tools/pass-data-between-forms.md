---
title: Passare dati tra form
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0c308169ef8a0f75821c669fb2cf6876d2b91b06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="pass-data-between-forms"></a>Passare dati tra form
Questa procedura dettagliata fornisce istruzioni passo-passo per il passaggio dei dati da un form a un altro. Usando le tabelle customers e orders di Northwind, un modulo consente agli utenti di selezionare un cliente e un secondo form vengono visualizzati gli ordini del cliente selezionato. Questa procedura dettagliata viene illustrato come creare un metodo nel secondo form che riceve i dati dal primo form.

> [!NOTE]
>  Questa procedura dettagliata illustra solo un modo per passare dati tra i form. Sono disponibili altre opzioni per passare dati a un form, incluse la creazione di un secondo costruttore per la ricezione di dati, oppure la creazione di una proprietà pubblica che può essere impostata con i dati dal primo form.

 Le attività illustrate nella procedura dettagliata sono le seguenti:

-   Creazione di un nuovo **Windows Forms Application** progetto.

-   Creazione e configurazione di un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

-   Selezione del controllo da creare sul form quando si trascinano elementi dal **origini dati** finestra. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Creazione di un controllo con associazione a dati trascinando elementi dal **origini dati** finestra in un form.

-   Creazione di un secondo form con una griglia per la visualizzazione dei dati.

-   Creazione di una query TableAdapter per recuperare gli ordini di uno specifico cliente.

-   Passaggio dei dati da un form all'altro.

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

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .

2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.

4. Denominare il progetto **PassingDataBetweenForms**, quindi scegliere **OK**.

     Il **PassingDataBetweenForms** progetto viene creato e aggiunto a **Esplora**.

## <a name="create-the-data-source"></a>Creare l'origine dati

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati** procedura guidata.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nel **scegliere un modello di database** verificare che **Dataset** è specificato e quindi fare clic su **Avanti**.

5.  Nel **Seleziona connessione dati** pagina, effettuare una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **nuova connessione** per avviare il **Aggiungi/Modifica connessione** la finestra di dialogo.

6.  Se il database è necessaria una password e se è abilitata l'opzione per includere dati riservati, selezionare l'opzione e quindi fare clic su **Avanti**.

7.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **Avanti**.

8.  Nel **Seleziona oggetti di Database** espandere la **tabelle** nodo.

9. Selezionare il **clienti** e **ordini** tabelle e quindi fare clic su **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e **clienti** e **ordini** tabelle vengono visualizzate nella **origini dati** finestra.

## <a name="create-the-first-form-form1"></a>Creare il primo form (Form1)
 È possibile creare una griglia con associazione a dati (un <xref:System.Windows.Forms.DataGridView> controllo), trascinando il **clienti** nodo dal **origini dati** finestra al form.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Per creare una griglia con associazione a dati nel form

-   Trascinare principale **clienti** nodo dal **origini dati** finestra **Form1**.

     Oggetto <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per l'esplorazione dei record vengono visualizzati nel **Form1**. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

## <a name="create-the-second-form-form2"></a>Creare il secondo form (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Per creare un secondo form al quale passare i dati

1.  Scegliere **Aggiungi Windows Form** dal menu **Progetto**.

2.  Lasciare il nome predefinito di **Form2**, fare clic su **Aggiungi**.

3.  Trascinare principale **ordini** nodo dal **origini dati** finestra **Form2**.

     Oggetto <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per l'esplorazione dei record vengono visualizzati nel **Form2**. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

4.  Eliminare il **OrdersBindingNavigator** dalla barra dei componenti.

     Il **OrdersBindingNavigator** scomparirà dalla **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Aggiungere una query TableAdapter a Form2 per caricare gli ordini del cliente selezionato nel Form1

#### <a name="to-create-a-tableadapter-query"></a>Per creare una query TableAdapter

1.  Fare doppio clic su di **NorthwindDataSet.xsd** file in **Esplora**.

2.  Fare doppio clic su di **OrdersTableAdapter**e selezionare **Aggiungi Query**.

3.  Lasciare l'opzione predefinita di **Usa istruzioni SQL**, quindi fare clic su **Avanti**.

4.  Lasciare l'opzione predefinita di **SELECT che restituisce righe**, quindi fare clic su **Avanti**.

5.  Aggiungere una clausola WHERE alla query, per restituire `Orders` in base il `CustomerID`. La query dovrebbe essere simile alla seguente:

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  Verificare che la sintassi dei parametri sia corretta per il database. In Microsoft Access, ad esempio, la clausola WHERE presenta la seguente sintassi: `WHERE CustomerID = ?`.

6.  Scegliere **Avanti**.

7.  Per il **immettere un nome di DataTableMethod**, tipo `FillByCustomerID`.

8.  Cancella il **Restituisci un DataTable** opzione e quindi fare clic su **Avanti**.

9. Scegliere **Fine**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Creare un metodo su Form2 al quale passare i dati

#### <a name="to-create-a-method-to-pass-data-to"></a>Per creare un metodo al quale passare i dati

1.  Fare doppio clic su **Form2**e selezionare **Visualizza codice** per aprire **Form2** nel **Editor di codice**.

2.  Aggiungere il seguente codice al **Form2** dopo il `Form2_Load` metodo:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Creare un metodo su Form1 per passare i dati e visualizzare Form2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Per creare un metodo per il passaggio dei dati a Form2

1.  In **Form1**, fare clic sulla griglia dati del cliente e quindi fare clic su **proprietà**.

2.  Nel **proprietà** finestra, fare clic su **eventi**.

3.  Fare doppio clic su di **CellDoubleClick** evento.

     Verrà visualizzato l'editor del codice.

4.  Aggiornare la definizione del metodo in modo che corrisponda all'esempio seguente:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>Esecuzione dell'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

-   Premere F5 per eseguire l'applicazione.

-   Fare doppio clic su un record del cliente in **Form1** per aprire **Form2** con gli ordini del cliente.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta passati i dati da un form all'altro. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

-   Aggiunta di funzionalità per il salvataggio dei dati nel database. Per ulteriori informazioni, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)