---
title: Creare un Windows Form per eseguire la ricerca di dati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d868002d2749dba2be378723a51560fc3c42c354
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-windows-form-to-search-data"></a>Creare un Windows Form per eseguire la ricerca di dati
Uno scenario applicativo comune prevede la visualizzazione dei dati selezionati in un form, ad esempio gli ordini per un determinato cliente o i dettagli di un ordine specifico. In questo scenario un utente immette informazioni in un form, quindi viene eseguita una query che usa come parametro l'input dell'utente. Questo significa che i dati vengono selezionati in base a una query con parametri. La query restituisce solo i dati che soddisfano i criteri immessi dall'utente. Questa procedura dettagliata illustra come creare una query che restituisca i clienti di una determinata città e come modificare l'interfaccia utente in modo che gli utenti possano immettere il nome di una città e fare clic su un pulsante per eseguire la query.

 L'uso di query con parametri rende più efficiente il funzionamento dell'applicazione, consentendo al database di eseguire in modo ottimale le operazioni di filtro rapido dei record. Al contrario, se richiesta un'intera tabella del database, trasferimento in rete e quindi utilizzare la logica dell'applicazione per trovare il record che si desidera, l'applicazione può diventare lento e inefficiente.

 È possibile aggiungere le query con parametri a qualsiasi oggetto TableAdapter e controlli per accettare i valori dei parametri ed eseguire la query, tramite il **generatore di criteri di ricerca** la finestra di dialogo. Aprire la finestra di dialogo selezionando il **Aggiungi Query** comando il **dati** menu (o da qualsiasi smart tag di TableAdapter).

 Le attività illustrate nella procedura dettagliata sono le seguenti:

-   Creazione di un nuovo progetto applicazione Windows Form.

-   Creazione e configurazione dell'origine dati nell'applicazione con il **configurazione guidata origine dati** procedura guidata.

-   Impostare il tipo di rilascio degli elementi di **origini dati**finestra.

-   Creazione di controlli che visualizzano dati trascinando elementi dal **origini dati** finestra in un form.

-   Aggiunta di controlli per la visualizzazione dei dati nel form.

-   Il completamento di **generatore di criteri di ricerca** la finestra di dialogo.

-   Immissione dei parametri nel form e l'esecuzione della query con parametri.

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
 Il primo passaggio consiste nel creare un **applicazione Windows Form**. Assegnazione di un nome per il progetto è facoltativa in questo passaggio, ma si sarà assegnargli un nome qui perché si sarà Salva il progetto in un secondo momento.

#### <a name="to-create-the-new-windows-forms-application-project"></a>Per creare il nuovo progetto applicazione Windows Form

1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .

2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.

4. Denominare il progetto **WindowsSearchForm**, quindi scegliere **OK**.

     Il **WindowsSearchForm** progetto viene creato e aggiunto a **Esplora**.

## <a name="create-the-data-source"></a>Creare l'origine dati
Questo passaggio consente di creare un'origine dati da un database tramite il **configurazione guidata origine dati** procedura guidata.

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati** procedura guidata.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nel **Seleziona connessione dati** eseguire pagina una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **nuova connessione** per avviare il **Aggiungi/Modifica connessione** la finestra di dialogo.

5.  Se il database richiede una password, selezionare l'opzione per includere dati riservati e quindi fare clic su **Avanti**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **Avanti**.

7.  Nel **Seleziona oggetti di Database** espandere la **tabelle** nodo.

8.  Selezionare il **clienti** tabella e quindi fare clic su **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e **clienti** tabella viene visualizzata nel **origini dati** finestra.

## <a name="create-the-form"></a>Creare il form
 È possibile creare i controlli con associazione a dati trascinando elementi dal **origini dati** finestra nel form.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form

1.  Espandere il **clienti** nodo il **origini dati** finestra.

2.  Trascinare il **clienti** nodo dal **origini dati** finestra al form.

     Sul form vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Aggiungere la parametrizzazione (funzionalità di ricerca) alla query
 È possibile aggiungere una clausola WHERE alla query originale utilizzando il **generatore di criteri di ricerca** la finestra di dialogo.

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Per creare una query con parametri e controlli per l'immissione dei parametri

1.  Selezionare il <xref:System.Windows.Forms.DataGridView> controllare e quindi scegliere **Aggiungi Query** sul **dati** menu.

2.  Tipo `FillByCity` nel **nuovo nome query** area il **generatore di criteri di ricerca** la finestra di dialogo.

3.  Aggiungere `WHERE City = @City` alla query nel **testo della Query** area.

     La query dovrebbe essere simile alla seguente:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    >  Origini dati Access e OLE DB utilizzano il punto interrogativo ('? ') per indicare i parametri, pertanto la clausola WHERE risulterebbe simile al seguente: `WHERE City = ?`.

4.  Fare clic su **OK** per chiudere la **generatore di criteri di ricerca** la finestra di dialogo.

     Oggetto **FillByCityToolStrip** viene aggiunto al form.

## <a name="testing-the-application"></a>Test dell'applicazione
 Quando l'applicazione viene eseguita, il form viene aperto ed è pronto ad accettare il parametro come input.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1.  Premere F5 per eseguire l'applicazione.

2.  Tipo **Londra** nel **Città** casella di testo e quindi fare clic su **FillByCity**.

     La griglia di dati viene popolata con i clienti che soddisfano i criteri. In questo esempio, la griglia dei dati vengono visualizzati solo i clienti che hanno un valore di **Londra** nella loro **Città** colonna.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form con parametri. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

-   Aggiunta di controlli per la visualizzazione di dati correlati. Per ulteriori informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)