---
title: Convalidare i dati in set di dati
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71d651d2e2d6c84b5858bb4687bf74aa503d014c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="validate-data-in-datasets"></a>Convalidare i dati in set di dati
Convalida dei dati è il processo di conferma che i valori immessi negli oggetti dati sono conformi ai vincoli all'interno dello schema di un set di dati. Il processo di convalida conferma inoltre che questi valori vengono eseguite le regole che sono state stabilite per l'applicazione. È buona norma convalidare i dati prima di inviare aggiornamenti al database sottostante. In questo modo si riduce gli errori, nonché il numero potenziale di round trip tra un'applicazione e il database.

È possibile confermare che i dati scritti in un set di dati siano validi creando i controlli di convalida nel set di dati stesso. Il set di dati è possibile controllare i dati indipendentemente dalla modalità di esecuzione dell'aggiornamento: direttamente dai controlli in un form, all'interno di un componente, o in altro modo. Poiché il set di dati fa parte dell'applicazione (a differenza di database back-end), è un punto logico per compilare la convalida delle specifiche dell'applicazione.

Il modo migliore per aggiungere la convalida per l'applicazione è nel file di classe parziale del set di dati. In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], aprire il **Progettazione Dataset** e fare doppio clic sulla colonna o tabella per cui si desidera creare la convalida. Questa azione crea automaticamente un <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> gestore dell'evento.

## <a name="validate-data"></a>Convalida dei dati
 Convalida all'interno di un set di dati può essere eseguita nei modi seguenti:

-   Creazione di convalida personalizzata specifica dell'applicazione in grado di verificare i valori in una colonna di dati singoli durante la modifica.  Per ulteriori informazioni, vedere [procedura: convalidare dati durante la modifica](validate-data-in-datasets.md).

-   Tramite la creazione di convalida personalizzata specifica dell'applicazione in grado di verificare i dati dei valori, mentre un intero data riga in fase di modifica. Per ulteriori informazioni, vedere [procedura: convalidare dati durante le modifiche riga](validate-data-in-datasets.md).

-   Creazione di chiavi, vincoli unique, e così via come parte della definizione di schema effettivo del set di dati.

-   Impostando le proprietà del <xref:System.Data.DataColumn> dell'oggetto, ad esempio <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, e <xref:System.Data.DataColumn.Unique%2A>.

Molti eventi vengono generati dal <xref:System.Data.DataTable> quando viene apportata una modifica in un record dell'oggetto:

-   Il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> vengono generati durante e dopo ogni modifica apportata a una singola colonna. Il <xref:System.Data.DataTable.ColumnChanging> evento è utile quando si desidera convalidare le modifiche in colonne specifiche. Informazioni sulla modifica proposta viene passate come argomento dell'evento.
-   Il <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> vengono generati durante e dopo qualsiasi modifica di una riga. Il <xref:System.Data.DataTable.RowChanging> evento è più generale. Indica che viene apportata una modifica in un punto qualsiasi nella riga, ma non si conosce la colonna da cui è stato modificato.

Per impostazione predefinita, ogni modifica apportata a una colonna genera pertanto quattro eventi. Il primo è il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> gli eventi per la colonna specifica da modificare. Quindi il <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventi. Se vengono apportate più modifiche alla riga, gli eventi vengono generati per ogni modifica.

> [!NOTE]
>  La riga di dati <xref:System.Data.DataRow.BeginEdit%2A> metodo disattiva il <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventi dopo la modifica di ogni singola colonna. In tal caso, l'evento non viene generato finché la <xref:System.Data.DataRow.EndEdit%2A> metodo è stato chiamato quando il <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> gli eventi vengono generati una sola volta. Per ulteriori informazioni, vedere [disattivare i vincoli durante la compilazione di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

L'evento che scelto dipende il livello di granularità si vuole essere la convalida. Se è importante intercettare un errore immediatamente quando viene modificata una colonna, è possibile compilare la convalida utilizzando il <xref:System.Data.DataTable.ColumnChanging> evento. In caso contrario, utilizzare il <xref:System.Data.DataTable.RowChanging> evento, che potrebbe comportare l'intercettazione di diversi errori in una sola volta. Inoltre, se i dati sono strutturati in modo che il valore di una colonna viene convalidato in base al contenuto di un'altra colonna, quindi eseguire la convalida durante la <xref:System.Data.DataTable.RowChanging> evento.

Quando vengono aggiornati i record, il <xref:System.Data.DataTable> oggetto genera gli eventi che è possibile rispondere durante e dopo aver apportato modifiche.

Se l'applicazione utilizza un dataset tipizzato, è possibile creare gestori eventi fortemente tipizzati. Che aggiungerà altri quattro eventi tipizzati che è possibile creare gestori per: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, e `dataTableNameRowDeleted`. Questi gestori eventi tipizzati passano un argomento che include i nomi delle colonne della tabella che rendono più facile leggere e scrivere codice.

## <a name="data-update-events"></a>Eventi di aggiornamento dati

|event|Descrizione|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Il valore in una colonna viene viene modificato. L'evento passa la riga e colonna, insieme al nuovo valore proposto.|
|<xref:System.Data.DataTable.ColumnChanged>|Il valore in una colonna è stato modificato. L'evento passa la riga e colonna, insieme al valore proposto.|
|<xref:System.Data.DataTable.RowChanging>|Le modifiche apportate a un <xref:System.Data.DataRow> oggetto sta per essere eseguito il commit nel dataset. Se non è stato chiamato il <xref:System.Data.DataRow.BeginEdit%2A> (metodo), il <xref:System.Data.DataTable.RowChanging> evento viene generato per ogni modifica apportata a una colonna immediatamente dopo il <xref:System.Data.DataTable.ColumnChanging> è stato generato l'evento. Se è stato chiamato <xref:System.Data.DataRow.BeginEdit%2A> prima di apportare modifiche, il <xref:System.Data.DataTable.RowChanging> evento viene generato solo quando si chiama il <xref:System.Data.DataRow.EndEdit%2A> metodo.<br /><br /> L'evento passa la riga, oltre a un valore che indica il tipo di azione (modifica, inserimento e così via) in corso.|
|<xref:System.Data.DataTable.RowChanged>|Una riga è stata modificata. L'evento passa la riga, oltre a un valore che indica il tipo di azione (modifica, inserimento e così via) in corso.|
|<xref:System.Data.DataTable.RowDeleting>|Eliminazione di una riga in corso. L'evento passa la riga, oltre a un valore che indica il tipo di azione (delete) in corso.|
|<xref:System.Data.DataTable.RowDeleted>|Una riga è stata eliminata. L'evento passa la riga, oltre a un valore che indica il tipo di azione (delete) in corso.|

Il <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, e <xref:System.Data.DataTable.RowDeleting> eventi vengono generati durante il processo di aggiornamento. È possibile utilizzare questi eventi per convalidare i dati o eseguire altri tipi di elaborazione. Poiché l'aggiornamento è in corso durante questi eventi, è possibile annullare generando un'eccezione, che impedisce l'aggiornamento da terminare.

Il <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> e <xref:System.Data.DataTable.RowDeleted> sono eventi di notifica che vengono generati quando l'aggiornamento è stato completato. Questi eventi sono utili quando si desidera eseguire un'ulteriore azione in base a un aggiornamento ha esito positivo.

## <a name="validate-data-during-column-changes"></a>Convalidare i dati durante la modifica delle colonne

> [!NOTE]
>  Il **Progettazione Dataset** crea una classe parziale in cui la convalida è possibile aggiungere logica per un set di dati. Il set di dati generato da progettazione non eliminare o modificare il codice nella classe parziale.

È possibile convalidare dati quando cambia il valore in una colonna di dati mediante la risposta per la <xref:System.Data.DataTable.ColumnChanging> evento. Quando generato, tale evento passa un argomento dell'evento (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) che contiene il valore proposto per la colonna corrente. In base al contenuto di `e.ProposedValue`, è possibile:

-   Accettare il valore proposto senza eseguire alcuna operazione.

-   Rifiutare il valore proposto impostando l'errore di colonna (<xref:System.Data.DataRow.SetColumnError%2A>) dall'interno del gestore eventi di modifica delle colonne.

-   Se si desidera utilizzare un <xref:System.Windows.Forms.ErrorProvider> viene visualizzato un messaggio di errore all'utente. Per ulteriori informazioni, vedere [sul componente ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

La convalida può essere eseguita anche durante la <xref:System.Data.DataTable.RowChanging> evento.

## <a name="validate-data-during-row-changes"></a>Convalidare i dati durante la modifica delle righe
È possibile scrivere codice per verificare che ogni colonna che si desidera convalidare contenga dati che soddisfi i requisiti dell'applicazione. Tale scopo, impostare la colonna per indicare la presenza di un errore se un valore proposto è accettabile. Negli esempi seguenti viene impostano un errore di colonna quando il `Quantity` colonna è pari o inferiore a 0. I gestori di eventi di modifica riga dovrebbero essere simile a nell'esempio seguente.

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Per convalidare dati quando una riga viene modificato (Visual Basic)

1.  Aprire il dataset nel **Progettazione Dataset**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Fare doppio clic sulla barra del titolo della tabella che si desidera convalidare. Questa azione crea automaticamente il <xref:System.Data.DataTable.RowChanging> gestore dell'evento del <xref:System.Data.DataTable> nel file di classe parziale del set di dati.

    > [!TIP]
    >  Fare doppio clic a sinistra del nome della tabella per creare il gestore dell'evento Modifica righe. Se si fa doppio clic sul nome della tabella, è possibile modificarlo.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>Per convalidare i dati quando una riga viene modificata (c#)

1.  Aprire il dataset nel **Progettazione Dataset**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Fare doppio clic sulla barra del titolo della tabella che si desidera convalidare. Questa azione crea un file di classe parziale per il <xref:System.Data.DataTable>.

    > [!NOTE]
    >  Il **Progettazione Dataset** non crea automaticamente un gestore eventi per il <xref:System.Data.DataTable.RowChanging> evento. È necessario creare un metodo per gestire il <xref:System.Data.DataTable.RowChanging> evento ed eseguire codice per associare l'evento nel metodo di inizializzazione della tabella.

3.  Copiare il codice seguente nella classe parziale:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Per recuperare le righe modificate
Ogni riga in una tabella di dati include un <xref:System.Data.DataRow.RowState%2A> proprietà che tiene traccia dello stato corrente della riga utilizzando i valori nel <xref:System.Data.DataRowState> enumerazione. È possibile restituire le righe modificate da una set di dati o una tabella dati chiamando il `GetChanges` metodo di un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>. È possibile verificare l'esistano di modifiche prima di chiamare `GetChanges` chiamando il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati.

> [!NOTE]
>  Dopo il commit delle modifiche per una set di dati o una tabella dati (chiamando il <xref:System.Data.DataSet.AcceptChanges%2A> metodo), il `GetChanges` metodo non restituisce alcun dato. Se l'applicazione deve elaborare le righe modificate, è necessario elaborare le modifiche prima di chiamare il `AcceptChanges` metodo.

La chiamata di <xref:System.Data.DataSet.GetChanges%2A> metodo di una set di dati o una tabella dati restituisce una nuovo set di dati o una tabella dati contenente solo i record che sono stati modificati. Se si desidera ottenere record specifici, ad esempio, solo i record nuovi o modificati, è possibile passare un valore compreso il <xref:System.Data.DataRowState> enumerazione come parametro per il `GetChanges` (metodo).

Utilizzare il <xref:System.Data.DataRowVersion> enumerazione per accedere alle diverse versioni di una riga (ad esempio, i valori originali in una riga prima della sua elaborazione).

#### <a name="to-get-all-changed-records-from-a-dataset"></a>Per ottenere tutti i record modificati da un set di dati

-   Chiamare il <xref:System.Data.DataSet.GetChanges%2A> metodo di un set di dati.

     L'esempio seguente crea un nuovo set di dati denominato `changedRecords` e la popola con tutti i record modificati da un altro set di dati denominato `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>Per ottenere tutti i record modificati da una tabella di dati

-   Chiamare il <xref:System.Data.DataTable.GetChanges%2A> metodo di un oggetto DataTable.

     L'esempio seguente crea una nuova tabella di dati denominata `changedRecordsTable` e la popola con tutti i record modificati da un'altra tabella di dati denominato `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Per ottenere tutti i record che hanno uno stato di riga specifico

-   Chiamare il `GetChanges` metodo di un set di dati o una tabella dati e passare un <xref:System.Data.DataRowState> il valore di enumerazione come argomento.

     Nell'esempio seguente viene illustrato come creare un nuovo set di dati denominato `addedRecords` e popolarla solo con i record che sono stati aggiunti i `dataSet1` set di dati.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Nell'esempio seguente viene illustrato come restituire tutti i record che sono stati aggiunti di recente per il `Customers` tabella:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Accedere alla versione originale di un DataRow
Quando vengono apportate modifiche alle righe di dati, il set di dati mantiene originale (<xref:System.Data.DataRowVersion.Original>) e new (<xref:System.Data.DataRowVersion.Current>) versioni della riga. Ad esempio, prima di chiamare il `AcceptChanges` (metodo), l'applicazione può accedere alle diverse versioni di un record (come definito nel <xref:System.Data.DataRowVersion> enumerazione) ed elaborare le modifiche di conseguenza.

> [!NOTE]
>  Versioni diverse di una riga esistano solo dopo che è stata modificata e prima che il `AcceptChanges` metodo è stato chiamato. Dopo il `AcceptChanges` metodo è stato chiamato, le versioni correnti e originali sono gli stessi.

Il passaggio di <xref:System.Data.DataRowVersion> valore insieme all'indice di colonna (o nome di colonna come una stringa) restituisce il valore della versione di riga specifica della colonna. La colonna modificata è identificata durante il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventi. Ciò è utile per controllare le versioni di riga diversi ai fini della convalida. Tuttavia, se è stata temporaneamente sospesa vincoli, questi eventi non verranno generati e sarà necessario a livello di programmazione di identificare le colonne modificate. È possibile farlo eseguendo un'iterazione attraverso il <xref:System.Data.DataTable.Columns%2A> insieme e confrontare i diversi <xref:System.Data.DataRowVersion> valori.

#### <a name="to-get-the-original-version-of-a-record"></a>Per ottenere la versione originale di un record

-   Accedere al valore di una colonna passando il <xref:System.Data.DataRowVersion> della riga di cui si desidera restituire.

     Nell'esempio seguente viene illustrato come utilizzare un <xref:System.Data.DataRowVersion> valore da ottenere il valore originale di un `CompanyName` campo in un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Accedere alla versione corrente di un DataRow

#### <a name="to-get-the-current-version-of-a-record"></a>Per ottenere la versione corrente di un record

-   Accedere al valore di una colonna e quindi aggiungere un parametro per l'indice che indica quale versione di una riga a cui si desidera restituire.

     Nell'esempio seguente viene illustrato come utilizzare un <xref:System.Data.DataRowVersion> valore da ottenere il valore corrente di un `CompanyName` campo in un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Procedura: Convalidare dati nel controllo DataGridView di Windows Form](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Procedura: Visualizzare le icone di errori per la convalida dei form con il componente ErrorProvider di Windows Form](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)