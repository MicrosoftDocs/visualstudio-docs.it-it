---
title: Connettersi ai dati in un database di Access (Windows Form)
ms.date: 09/15/2017
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: da00528f7c5e2332f4aa599674f6dcb0929be125
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Connettersi ai dati in un database di Access (Windows Form)
È possibile connettersi a un database di Access (file con estensione mdf o un file con estensione accdb) tramite Visual Studio. Dopo aver definito la connessione, i dati visualizzati nel **origini dati** finestra. da cui è possibile trascinare tabelle o visualizzazioni nei form.

## <a name="prerequisites"></a>Prerequisiti
 Per utilizzare queste procedure, è necessario un progetto di applicazione Windows Form e un database di Access (file con estensione accdb) o un database Access 2000-2003 (file con estensione mdb). Attenersi alla procedura che corrisponde al tipo di file utilizzato.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Creazione di set di dati per un file con estensione accdb
 È possibile connettersi ai database creati tramite Access 2013, Office 365, Access 2010 o Access 2007 tramite la procedura seguente.

#### <a name="to-create-the-dataset"></a>Per creare il dataset

1.  Aprire l'applicazione Windows Form a cui si desidera connettere i dati.

2.  Nel **vista** dal menu **altre finestre** > **origini dati**.

     ![Visualizza, altre origini dati di Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     Il **configurazione guidata origine dati** apre.

4.  Selezionare **Database** sul **scegliere un tipo di origine dati** pagina e quindi selezionare **Avanti**.

5.  Selezionare **Dataset** sul **scegliere un modello di Database** pagina e quindi selezionare **Avanti**.

6.  Nel **Seleziona connessione dati** selezionare **nuova connessione** per configurare una nuova connessione dati.

     Il **Aggiungi connessione** verrà visualizzata la finestra di dialogo.

7.  Selezionare il **modifica** accanto al pulsante il **origine dati** casella di testo.

     Il **Modifica origine dati** verrà visualizzata la finestra di dialogo.

8.  Nell'elenco di origini dati, scegliere  **\<altri\>**. Nel **provider di dati** elenco a discesa, selezionare **il Provider di dati .NET Framework per OLE DB**, quindi scegliere **OK**.

9. Nel **Aggiungi connessione** nella finestra di dialogo **Microsoft Office 12.0 Access Database Engine OLE DB Provider** dal **Provider OLE DB** elenco a discesa.

     ![OLE DB Provider Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

     > [!NOTE]
     >  Se non viene visualizzato **Microsoft Office 12.0 Access Database Engine OLE DB Provider** nell'elenco a discesa del provider OLE DB, è necessario installare il [2007 Office System Driver: Data Connectivity Components](https://www.microsoft.com/download/confirmation.aspx?id=23734).

9. Nel **nome file o Server** casella di testo, specificare il percorso e nome del file con estensione accdb a cui connettersi, quindi fare clic **OK**. (Se il file di database ha un nome utente e una password, specificare le prima di selezionare **OK**.)

10. Selezionare **Avanti** sul **Seleziona connessione dati** pagina.

     È possibile ottenere una finestra di dialogo indicante che il file di dati non è presente nel progetto corrente. Selezionare **Sì** o **No**.

11. Selezionare **Avanti** sul **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.

12. Espandere il **tabelle** nodo il **Seleziona oggetti di Database** pagina.

13. Selezionare le tabelle o viste desiderato nel set di dati e quindi selezionare **fine**.

     Il dataset viene aggiunto al progetto e le tabelle e viste visualizzate nel **origini dati** finestra.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Creazione di set di dati per un file con estensione mdb
 Il dataset viene creato eseguendo la **configurazione guidata origine dati**.

#### <a name="to-create-the-dataset"></a>Per creare il dataset

1.  Aprire l'applicazione Windows Form a cui si desidera connettere i dati.

2.  Nel **vista** dal menu **altre finestre** > **origini dati**.

     ![Visualizza, altre origini dati di Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     Il **configurazione guidata origine dati** apre.

4.  Selezionare **Database** sul **scegliere un tipo di origine dati** pagina e quindi selezionare **Avanti**.

5.  Selezionare **Dataset** sul **scegliere un modello di Database** pagina e quindi selezionare **Avanti**.

6.  Nel **Seleziona connessione dati** selezionare **nuova connessione** per configurare una nuova connessione dati.

7.  Se l'origine dati non è **File di Database Microsoft Access (OLE DB)**selezionare **modifica** per aprire la **Modifica origine dati** la finestra di dialogo e selezionare **Microsoft Accedere al File di Database**, quindi selezionare **OK**.

8.  Nel **nome file di Database**, specificare il percorso e nome del file con estensione mdb che si desidera connettersi e quindi selezionare **OK**.

     ![Aggiungere File di Database di Access connessione](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Selezionare **Avanti** sul **Seleziona connessione dati** pagina.

10. Selezionare **Avanti** sul **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.

11. Espandere il **tabelle** nodo il **Seleziona oggetti di Database** pagina.

12. Selezionare le tabelle o viste desiderato nel set di dati e quindi selezionare **fine**.

     Il dataset viene aggiunto al progetto e le tabelle e viste visualizzate nel **origini dati** finestra.

## <a name="security"></a>Sicurezza
 L'archiviazione di informazioni riservate, ad esempio una password, può avere implicazioni sulla sicurezza dell'applicazione. L'autenticazione di Windows, detta anche sicurezza integrata, consente di controllare l'accesso a un database in modo più sicuro. Per altre informazioni, vedere [Protezione delle informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Passaggi successivi
 Il set di dati appena creato è ora disponibile nel **origini dati** finestra. È ora possibile eseguire le operazioni seguenti:

-   Selezionare gli elementi di **origini dati** finestra e trascinarli nel form (vedere [controlli binding di Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

-   Aprire l'origine dati nel **Progettazione Dataset** per aggiungere o modificare gli oggetti che costituiscono il set di dati.

-   Aggiungere la logica di convalida per il <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> evento delle tabelle di dati nel set di dati (vedere [convalidare i dati in set di dati](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Vedere anche

- [Aggiungere connessioni](../data-tools/add-new-connections.md)