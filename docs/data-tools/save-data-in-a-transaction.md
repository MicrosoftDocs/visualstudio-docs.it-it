---
title: 'Procedura dettagliata: Salvataggio di dati in una transazione'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6fd36ace8949774c755a7a192e201b6d9011ff8b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Procedura dettagliata: Salvataggio di dati in una transazione
Questa procedura dettagliata viene illustrato come salvare dati in una transazione utilizzando il <xref:System.Transactions> dello spazio dei nomi. In questa procedura dettagliata si creerà un'applicazione Windows Form. Utilizzare la configurazione guidata origine dati per creare un set di dati per le due tabelle nel database di esempio Northwind. Viene aggiunta a controlli con associazione dati a un Windows form, e che si desidera modificare il codice di BindingNavigator pulsante Salva aggiornare il database all'interno di un TransactionScope.

## <a name="prerequisites"></a>Prerequisiti
Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **lo sviluppo desktop .NET** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .

       Verrà visualizzata una finestra dell'editor di query.

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Form
 Il primo passaggio consiste nel creare un **applicazione Windows Form**.

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .

2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.

4. Denominare il progetto **SavingDataInATransactionWalkthrough**, quindi scegliere **OK**.

     Il **SavingDataInATransactionWalkthrough** progetto viene creato e aggiunto a **Esplora**.

## <a name="create-a-database-data-source"></a>Creare un'origine dati di database
 Questo passaggio viene utilizzata la **configurazione guidata origine dati** per creare un'origine dati basata sul `Customers` e `Orders` tabelle nel database di esempio Northwind.

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1.  Nel **dati** dal menu **Mostra origini dati**.

2.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati**.

3.  Nel **scegliere un tipo di origine dati** selezionare **Database**, quindi selezionare **Avanti**.

4.  Nel **Seleziona connessione dati** eseguire schermata una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         oppure

    -   Selezionare **nuova connessione** per avviare il **Aggiungi/Modifica connessione** finestra di dialogo e creare una connessione al database Northwind.

5.  Se il database richiede una password, selezionare l'opzione per includere dati riservati, quindi selezionare **Avanti**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti**.

7.  Nel **Seleziona oggetti di Database** schermata, quindi espandere il **tabelle** nodo.

8.  Selezionare il `Customers` e `Orders` tabelle e quindi selezionare **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e `Customers` e `Orders` tabelle vengono visualizzate nella **origini dati** finestra.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form
 È possibile creare i controlli con associazione a dati trascinando elementi dal **origini dati** finestra nel form.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare i dati associati a controlli in Windows form

-   Nel **origini dati** finestra, espandere il **clienti** nodo.

-   Trascinare principale **clienti** nodo dal **origini dati** finestra **Form1**.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

-   Trascinare correlata **ordini** nodo (non principale **ordini** nodo, ma il nodo della tabella figlio correlata seguente il **Fax** colonna) nel form sotto la  **CustomersDataGridView**.

     Nel form verrà visualizzato un oggetto <xref:System.Windows.Forms.DataGridView>. Un `OrdersTableAdapter` e <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Aggiungere un riferimento all'assembly System. Transactions
 Le transazioni usano lo spazio dei nomi <xref:System.Transactions>. Un riferimento di progetto all'assembly system.transactions non viene aggiunto per impostazione predefinita. Pertanto, è necessario aggiungerlo manualmente.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Per aggiungere un riferimento al file DLL System.Transactions.

1.  Nel **progetto** dal menu **Aggiungi riferimento**.

2.  Selezionare **System. Transactions** (sul **.NET** scheda), quindi selezionare **OK**.

     Un riferimento a **System. Transactions** viene aggiunto al progetto.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modificare il codice nel pulsante SaveItem di BindingNavigator
 Per la prima tabella rilasciata nel form, viene aggiunto codice per impostazione predefinita per il `click` pulsante evento del Salva il <xref:System.Windows.Forms.BindingNavigator>. È necessario aggiungere manualmente il codice per aggiornare eventuali tabelle aggiuntive. Questa procedura dettagliata, viene effettuato il refactoring del codice di salvataggio salvataggio gestore dell'evento click del pulsante. È inoltre possibile creare altri metodi per fornire funzionalità di aggiornamento specifico in base alle necessità della riga deve essere aggiunto o eliminato.

#### <a name="to-modify-the-auto-generated-save-code"></a>Per modificare il codice di salvataggio autogenerato

1.  Selezionare il **salvare** pulsante il **CustomersBindingNavigator** (il pulsante con l'icona del disco floppy).

2.  Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

L'ordine di riconciliazione delle modifiche ai dati correlati è il seguente:

-   Eliminare i record figlio. (In questo caso, eliminare i record di `Orders` tabella.)

-   Eliminare i record padre. (In questo caso, eliminare i record di `Customers` tabella.)

-   Inserire i record padre. (In questo caso, inserire i record nella `Customers` tabella.)

-   Inserire i record figlio. (In questo caso, inserire i record nella `Orders` tabella.)

#### <a name="to-delete-existing-orders"></a>Per eliminare gli ordini esistenti

-   Aggiungere il seguente `DeleteOrders` metodo **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

#### <a name="to-delete-existing-customers"></a>Per eliminare i clienti esistenti

-   Aggiungere il seguente `DeleteCustomers` metodo **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

#### <a name="to-add-new-customers"></a>Per aggiungere nuovi clienti

-   Aggiungere il seguente `AddNewCustomers` metodo **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

#### <a name="to-add-new-orders"></a>Per aggiungere nuovi ordini

-   Aggiungere il seguente `AddNewOrders` metodo **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Esecuzione dell'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

-   Selezionare **F5** per eseguire l'applicazione.

## <a name="see-also"></a>Vedere anche

- [Procedura: salvare dati utilizzando una transazione](../data-tools/save-data-by-using-a-transaction.md)
- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)