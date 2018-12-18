---
title: Creare un file di database e usare Progettazione tabelle in Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 305374cbce519a87f1d40e09efac7f490b28fe0d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Creare un database e aggiungere tabelle in Visual Studio
È possibile utilizzare Visual Studio per creare e aggiornare i file di database locale di SQL Server Express LocalDB. È anche possibile creare un database tramite l'esecuzione di istruzioni Transact-SQL nel **Esplora oggetti di SQL Server** finestra degli strumenti in Visual Studio. In questo argomento, si sarà creare un file con estensione mdf e aggiungere tabelle e le chiavi utilizzando Progettazione tabelle.

## <a name="prerequisites"></a>Prerequisiti
Per completare questa procedura dettagliata, è necessario disporre facoltativo **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio installato. Per installarlo, aprire **programma di installazione di Visual Studio** e scegliere il **i carichi di lavoro** scheda. In **Web e Cloud**, scegliere **l'elaborazione e archiviazione dei dati**. Scegliere il **modifica** pulsante per aggiungere il carico di lavoro per Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Creare un progetto e un file di database locale

### <a name="to-create-a-project-and-a-database-file"></a>Per creare un progetto e un file di database
1.  Creare un progetto Windows Form denominato `SampleDatabaseWalkthrough`.

2.  Nella barra dei menu, selezionare **progetto**, **Aggiungi nuovo elemento**.

3.  Nell'elenco dei modelli di elemento, scorrere verso il basso e selezionare **Database basato sul servizio**.

     ![Finestra di dialogo modelli di elemento](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4.  Nome del database **SampleDatabase**, quindi selezionare il **Aggiungi** pulsante.

### <a name="to-add-a-data-source"></a>Per aggiungere un'origine dati
5.  Se il **origini dati** finestra non è aperta, aprirla scegliendo il **Maiusc + Alt + D** chiavi oppure sulla barra dei menu, selezionare **vista**, **altre finestre**, **Origini dati**.

6.  Nel **origini dati** finestra, seleziona il **Aggiungi nuova origine dati** collegamento.

    Il **configurazione guidata origine dati** apre.

7. Nel **scegliere un tipo di origine dati** pagina, scegliere **Database** e quindi scegliere **Avanti**.

8. Nel **scegliere un modello di Database** pagina, scegliere **Avanti** per accettare il valore predefinito (set di dati).

9. Nel **Seleziona connessione dati** pagina, selezionare il **SampleDatabase.mdf** file nell'elenco a discesa e quindi scegliere **Avanti**.

10. Nel **Salva stringa di connessione al File di configurazione dell'applicazione** pagina, scegliere **Avanti**.

11. Uno di **Seleziona oggetti di Database** pagina, verrà visualizzato un messaggio che segnala il database non contiene tutti gli oggetti. Scegliere **Fine**.

### <a name="to-view-properties-of-the-data-connection"></a>Per visualizzare le proprietà della connessione dati
È possibile visualizzare la stringa di connessione per il file SampleDatabase.mdf, aprire la finestra delle proprietà della connessione dati:

-   In Visual Studio, selezionare **vista**, **Esplora oggetti di SQL Server** se tale finestra non è già aperta. Aprire la finestra Proprietà espandere il **connessioni dati** nodo, aprire il menu di scelta rapida per il file SampleDatabase.mdf e quindi selezionando **proprietà**.

-   In alternativa, è possibile selezionare **vista**, **Esplora Server**, se tale finestra non è già aperta. Aprire la finestra Proprietà espandere il **connessioni dati** nodo. Aprire il menu di scelta rapida per il file SampleDatabase.mdf e quindi selezionare **proprietà**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Creare tabelle e le chiavi tramite Progettazione tabelle
In questa sezione, si creeranno due tabelle, una chiave primaria in ogni tabella e alcune righe di dati di esempio. Si creerà inoltre una chiave esterna per specificare quali record di una tabella corrispondere ai record di altra tabella.

### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers
1.  In **Esplora Server** o **Esplora oggetti di SQL Server**, espandere il **connessioni dati** nodo, quindi espandere il **SampleDatabase.mdf**nodo.

2.  Aprire il menu di scelta rapida per **tabelle**, quindi selezionare **Aggiungi nuova tabella**.

     Il **Progettazione tabelle** apre e visualizza una griglia con una riga predefinita, che rappresenta una singola colonna della tabella che si sta creando. Aggiungendo righe alla griglia, vengono aggiunte colonne alla tabella.

3.  Nella griglia, aggiungere una riga per ognuna delle seguenti voci:

    |Nome colonna|Tipo di dati|Consente valori null|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (deselezionato)|
    |`CompanyName`|`nvarchar(50)`|False (deselezionato)|
    |`ContactName`|`nvarchar (50)`|True (selezionato)|
    |`Phone`|`nvarchar (24)`|True (selezionato)|

4.  Aprire il menu di scelta rapida per il `CustomerID` di riga e quindi selezionare **Imposta chiave primaria**.

5.  Aprire il menu di scelta rapida per la riga predefinita e quindi selezionare **eliminare**.

6.  Denominare la tabella Customers aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

    Viene visualizzato un output simile al seguente:

    ![Progettazione tabelle](../data-tools/media/raddata-table-designer.png "raddata Progettazione tabelle")

7.  Nell'angolo superiore sinistro del **Progettazione tabelle**, selezionare il **aggiornamento** pulsante.

8.  Nel **Anteprima aggiornamenti Database** la finestra di dialogo, seleziona il **aggiornamento Database** pulsante.

    Le modifiche vengono salvate nel file del database locale.

### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders
1.  Aggiungere un'altra tabella, quindi aggiungere una riga per ogni voce nella tabella seguente:

    |Nome colonna|Tipo di dati|Consente valori null|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (deselezionato)|
    |`CustomerID`|`nchar(5)`|False (deselezionato)|
    |`OrderDate`|`datetime`|True (selezionato)|
    |`OrderQuantity`|`int`|True (selezionato)|

2.  Impostare **OrderID** come chiave primaria e quindi eliminare la riga predefinita.

3.  Denominare la tabella Orders aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4.  Nell'angolo superiore sinistro del **Progettazione tabelle**, selezionare il **aggiornamento** pulsante.

5.  Nel **Anteprima aggiornamenti Database** la finestra di dialogo, seleziona il **aggiornamento Database** pulsante.

    Le modifiche vengono salvate nel file del database locale.

### <a name="to-create-a-foreign-key"></a>Per creare una chiave esterna
1.  Nel riquadro contesto sul lato destro della griglia, aprire il menu di scelta rapida per **chiavi esterne**, quindi selezionare **Aggiungi nuova chiave esterna**, come mostrato nella figura seguente.

     ![Aggiunta di una chiave esterna in Progettazione tabelle](../data-tools/media/foreignkey.png "ForeignKey")

2.  Nella casella di testo che viene visualizzata, sostituire **ToTable** con `Customers`.

3.  Nel riquadro T-SQL, aggiornare l'ultima riga affinché corrisponda all'esempio seguente:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4.  Nell'angolo superiore sinistro del **Progettazione tabelle**, selezionare il **aggiornamento** pulsante.

5.  Nel **Anteprima aggiornamenti Database** la finestra di dialogo, seleziona il **aggiornamento Database** pulsante.

    Le modifiche vengono salvate nel file del database locale.

## <a name="populate-the-tables-with-data"></a>Popolare le tabelle con dati

### <a name="to-populate-the-tables-with-data"></a>Per inserire dati nelle tabelle

1.  In **Esplora Server** o **Esplora oggetti di SQL Server**, espandere il nodo per il database di esempio.

2.  Aprire il menu di scelta rapida per il **tabelle** nodo, seleziona **aggiornamento**, quindi espandere il **tabelle** nodo.

3.  Aprire il menu di scelta rapida per la tabella Customers e quindi selezionare **Mostra dati tabella**.

4.  Aggiungere i dati desiderati per alcuni clienti.

    È possibile specificare tutti i cinque caratteri desiderati come ID cliente, ma sceglierne almeno uno da ricordare in un secondo momento per l'utilizzo in questa procedura.

5.  Aprire il menu di scelta rapida per la tabella Orders e quindi selezionare **Mostra dati tabella**.

6.  Aggiungere i dati per alcuni ordini.

    > [!IMPORTANT]
    > Assicurarsi che tutti gli ID degli ordini e quantitativi sono numeri interi e che ogni ID cliente corrisponda un valore specificato nella colonna CustomerID della tabella Customers.

7.  Nella barra dei menu, selezionare **File**, **Salva tutto**.

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)