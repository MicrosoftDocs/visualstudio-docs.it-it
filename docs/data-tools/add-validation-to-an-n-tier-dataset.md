---
title: Aggiungere la convalida a un dataset a più livelli
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ed9bcb4521b5e9bdad839563aae1c566d20a5681
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Aggiungere la convalida a un dataset a più livelli
Aggiunta della convalida a un set di dati separato in una soluzione a più livelli è fondamentalmente uguale all'aggiunta di convalida per un singolo file (un dataset in un unico progetto). È il percorso suggerito per eseguire la convalida dei dati durante il <xref:System.Data.DataTable.ColumnChanging> e/o <xref:System.Data.DataTable.RowChanging> gli eventi di una tabella dati.

 Il set di dati fornisce la funzionalità per creare classi parziali a cui è possibile aggiungere il codice utente per gli eventi di modifica delle righe e colonne delle tabelle di dati nel set di dati. Per ulteriori informazioni sull'aggiunta di codice a un set di dati in una soluzione a più livelli, vedere [aggiungere codice al set di dati nelle applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md), e [aggiungere codice agli oggetti TableAdapter nelle applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Per ulteriori informazioni sulle classi parziali, vedere [procedura: suddividere una classe in classi parziali (Progettazione classi)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) o [classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
>  Quando si separano i DataSet dai TableAdapter (impostando il **progetto DataSet** proprietà), classi parziali del dataset esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.

> [!NOTE]
>  Progettazione dataset non crea automaticamente i gestori eventi in c# per il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> eventi. È necessario creare un gestore eventi e associare il gestore eventi all'evento sottostante manualmente. Le procedure seguenti viene descritto come creare i gestori eventi necessari in Visual Basic e c#.

## <a name="validate-changes-to-individual-columns"></a>Convalidare le modifiche alle singole colonne
 Convalidare i valori delle singole colonne gestendo il <xref:System.Data.DataTable.ColumnChanging> evento. Il <xref:System.Data.DataTable.ColumnChanging> evento viene generato quando viene modificato un valore in una colonna. Creare un gestore eventi per il <xref:System.Data.DataTable.ColumnChanging> evento facendo doppio clic su colonna desiderata nel **Progettazione Dataset**.

 La prima volta che si fa doppio clic su una colonna, la finestra di progettazione genera un gestore eventi per il <xref:System.Data.DataTable.ColumnChanging> evento. Un `If...Then` l'istruzione viene creata anche la verifica di una colonna specifica. Ad esempio, il codice seguente viene generato quando si fa doppio clic sulla tabella Orders di Northwind colonna RequiredDate:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
>  Nei progetti c#, la finestra di progettazione del set di dati crea solo classi parziali per il set di dati e le singole tabelle nel set di dati. Progettazione Dataset non crea automaticamente i gestori eventi per il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> gli eventi in c# come invece avviene in Visual Basic. Nei progetti c#, è necessario creare manualmente un metodo per gestire l'evento e associare il metodo per l'evento sottostante. La procedura seguente fornisce i passaggi per creare i gestori eventi necessari in Visual Basic e c#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Per aggiungere la convalida durante la modifica di valori delle singole colonne

1.  Aprire il set di dati facendo doppio clic il **XSD** file **Esplora**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Fare doppio clic sulla colonna che si desidera convalidare. Questa azione crea il <xref:System.Data.DataTable.ColumnChanging> gestore dell'evento.

    > [!NOTE]
    >  Progettazione Dataset non crea automaticamente un gestore eventi per l'evento c#. Il codice che è necessario gestire l'evento in c# è incluso nella sezione successiva. `SampleColumnChangingEvent` viene creato e quindi collegato al <xref:System.Data.DataTable.ColumnChanging> eventi nel <xref:System.Data.DataTable.EndInit%2A> metodo.

3.  Aggiungere il codice per verificare che `e.ProposedValue` contiene dati che soddisfi i requisiti dell'applicazione. Se il valore proposto è inaccettabile, impostare la colonna per indicare la presenza di un errore.

     Esempio di codice seguente consente di verificare che il **quantità** colonna contiene un valore maggiore di 0. Se **quantità** è minore o uguale a 0, la colonna è impostata su un errore. Il `Else` clausola cancella l'errore se **quantità** è maggiore di 0. Il codice nel gestore dell'evento di modifica colonna sarà simile al seguente:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```
    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Convalidare le modifiche a intere righe
 Convalidare i valori in intere righe gestendo il <xref:System.Data.DataTable.RowChanging> evento. Il <xref:System.Data.DataTable.RowChanging> evento viene generato quando vengono applicati i valori in tutte le colonne. È necessario eseguire la convalida mediante il <xref:System.Data.DataTable.RowChanging> eventi quando il valore in una colonna si basa sul valore di un'altra colonna. Si consideri ad esempio OrderDate e RequiredDate nella tabella Orders di Northwind.

 Quando vengono immesse ordini, la convalida garantisce che un ordine non sia stato immesso con un valore RequiredDate uguale o precedente OrderDate. In questo esempio, i valori per le colonne OrderDate sia RequiredDate necessario confrontare, pertanto la convalida di una singola modifica di colonna non ha senso.

 Creare un gestore eventi per il <xref:System.Data.DataTable.RowChanging> evento facendo doppio clic sul nome della tabella nella barra del titolo della tabella nel **Progettazione Dataset**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Per aggiungere la convalida durante la modifica a intere righe

1.  Aprire il set di dati facendo doppio clic il **XSD** file **Esplora**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Fare doppio clic sulla barra del titolo della tabella di dati nella finestra di progettazione.

     Una classe parziale viene creata con un `RowChanging` gestore dell'evento e viene aperta nell'Editor di codice.

    > [!NOTE]
    >  Progettazione Dataset non crea automaticamente un gestore eventi per il <xref:System.Data.DataTable.RowChanging> eventi nei progetti c#. È necessario creare un metodo per gestire il <xref:System.Data.DataTable.RowChanging> evento e eseguire codice quindi associare l'evento nel metodo di inizializzazione della tabella.

3.  Aggiungere il codice utente all'interno della dichiarazione di classe parziale.

4.  Il codice seguente viene illustrato dove aggiungere il codice utente per la convalida durante la <xref:System.Data.DataTable.RowChanging> evento. L'esempio c# include anche il codice per associare il metodo del gestore eventi, fino al `OrdersRowChanging` evento.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```
    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Vedere anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md)