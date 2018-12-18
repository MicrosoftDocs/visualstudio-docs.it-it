---
title: Modificare i dati in set di dati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f9acc81270ecf9c0dfc60d3e1cfed524e0ce97f5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="edit-data-in-datasets"></a>Modificare i dati in set di dati
Modificare i dati nelle tabelle di dati proprio come si modificano i dati in una tabella in qualsiasi database. Il processo può includere inserimento, aggiornamento ed eliminazione di record nella tabella. In un form associato a dati, è possibile specificare quali campi sono modificabili dall'utente. In questi casi, l'infrastruttura di associazione di dati gestisce tutto il rilevamento delle modifiche in modo che le modifiche possono essere inviate al database in un secondo momento. Se si apportano modifiche ai dati a livello di codice e si desidera inviare le modifiche al database, è necessario utilizzare gli oggetti e metodi che eseguono il rilevamento delle modifiche per l'utente.

Oltre a modificare i dati effettivi, è inoltre possibile cercare un <xref:System.Data.DataTable> per restituire righe di dati specifiche. Ad esempio, potrebbe eseguire query per singole righe, versioni specifiche di righe (originali e proposte), le righe che sono stati modificati o le righe che contengono errori.

## <a name="to-edit-rows-in-a-dataset"></a>Per modificare le righe in un set di dati
Per modificare una riga esistente in un <xref:System.Data.DataTable>, è necessario individuare il <xref:System.Data.DataRow> che si desidera modificare e quindi assegnare i valori aggiornati per le colonne desiderate.

Se non si conosce l'indice della riga di cui si desidera utilizzare modificare il `FindBy` metodo effettuare la ricerca della chiave primaria:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Se si conosce l'indice di riga, sia possibile accedere e modifica le righe come indicato di seguito:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Per inserire nuove righe in un set di dati
Le applicazioni che utilizzano i controlli associati a dati in genere aggiungono nuovi record mediante il **Aggiungi nuovo** pulsante un [controllo BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Per aggiungere manualmente i nuovi record per un set di dati, creare una nuova riga di dati chiamando il metodo nella DataTable. Quindi aggiungere la riga di <xref:System.Data.DataRow> raccolta (<xref:System.Data.DataTable.Rows%2A>) del <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Per conservare le informazioni necessarie per inviare gli aggiornamenti all'origine dati di set di dati, utilizzare il <xref:System.Data.DataRow.Delete%2A> metodo per rimuovere le righe in una tabella dati. Ad esempio, se l'applicazione utilizza un oggetto TableAdapter (o <xref:System.Data.Common.DataAdapter>), dell'oggetto TableAdapter `Update` metodo elimina le righe nel database contenenti un <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState.Deleted>.

Se l'applicazione non è necessario inviare gli aggiornamenti a un'origine dati, quindi è possibile rimuovere i record accedendo direttamente la raccolta di righe di dati (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Per eliminare i record da una tabella dati

-   Chiamare il <xref:System.Data.DataRow.Delete%2A> metodo di un <xref:System.Data.DataRow>.

     Questo metodo non rimuove fisicamente il record. In alternativa, contrassegna il record per l'eliminazione.

    > [!NOTE]
    >  Se si ottiene la proprietà count di un <xref:System.Data.DataRowCollection>, il numero risultante include i record contrassegnati per l'eliminazione. Per ottenere un conteggio accurato di record che non sono contrassegnati per l'eliminazione, è possibile scorrere in ciclo raccolta esaminando il <xref:System.Data.DataRow.RowState%2A> proprietà di ogni record. (Record contrassegnati per l'eliminazione presentano un <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState.Deleted>.) In alternativa, è possibile creare una visualizzazione di dati di un set di dati che i filtri in base allo stato di riga e ottenere la proprietà count da qui.

Nell'esempio seguente viene illustrato come chiamare il <xref:System.Data.DataRow.Delete%2A> metodo per contrassegnare la prima riga di `Customers` tabella come eliminati:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Determinare se sono presenti righe modificate
Quando vengono apportate modifiche ai record in un set di dati, informazioni su tali modifiche vengono archiviate fino a quando non si esegue il commit. Commit delle modifiche quando si chiama il `AcceptChanges` metodo di una set di dati o una tabella dati o quando si chiama il `Update` metodo di un oggetto TableAdapter o un adattatore dati.

Le modifiche vengono rilevati e due i modi in ogni riga di dati:

-   Ogni riga di dati contiene informazioni relative ai relativi <xref:System.Data.DataRow.RowState%2A> (ad esempio, <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, o <xref:System.Data.DataRowState.Unchanged>).

-   Ogni riga di dati modificati contiene più versioni di riga (<xref:System.Data.DataRowVersion>), la versione originale (prima delle modifiche) e la versione corrente (dopo aver apportato modifiche). Durante il periodo durante cui è in sospeso una modifica (l'ora in cui è possibile rispondere al <xref:System.Data.DataTable.RowChanging> eventi), una terza versione, versione proposta, è disponibile.

Il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati restituisce `true` se sono state apportate modifiche nel set di dati. Dopo aver determinato l'esistano di righe modificate, è possibile chiamare il `GetChanges` metodo di un <xref:System.Data.DataSet> o <xref:System.Data.DataTable> per restituire un set di righe modificate.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Per determinare se sono state apportate modifiche alle righe

-   Chiamare il <xref:System.Data.DataSet.HasChanges%2A> metodo per verificare la presenza di un set di dati delle righe modificate.

Nell'esempio seguente viene illustrato come controllare il valore restituito dal <xref:System.Data.DataSet.HasChanges%2A> metodo per rilevare se sono presenti tutte le righe modificate in un set di dati denominato `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Determinare il tipo di modifiche
È inoltre possibile controllare per vedere il tipo di modifiche apportate in un set di dati passando un valore di <xref:System.Data.DataRowState> enumerazione per il <xref:System.Data.DataSet.HasChanges%2A> (metodo).

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Per determinare il tipo di modifiche sono state apportate a una riga

-   Passare un <xref:System.Data.DataRowState> valore per il <xref:System.Data.DataSet.HasChanges%2A> metodo.

Nell'esempio seguente viene illustrato come controllare un set di dati denominato `NorthwindDataset1` per stabilire se sono state aggiunte nuove righe a esso:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Per individuare le righe che contengono errori
Quando si utilizzano le singole colonne e righe di dati, possono verificarsi errori. È possibile controllare il `HasErrors` proprietà per determinare se sono presenti errori un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow>.

1.  Controllare il `HasErrors` proprietà per verificare se sono presenti errori nel set di dati.

2.  Se il `HasErrors` proprietà `true`, scorrere le raccolte di tabelle, quindi il tramite le righe, per trovare la riga con l'errore.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)