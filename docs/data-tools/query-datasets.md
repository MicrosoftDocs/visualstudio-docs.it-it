---
title: Set di dati di query
description: Informazioni sui set di impostazioni di query. Informazioni sulla distinzione tra maiuscole e minuscole. Trovare una riga specifica in una tabella di dati, trovare righe in base ai valori di colonna e accedere ai record correlati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c5f085cae185a48f3d41c6fa4bca5cad7afb46b3
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215799"
---
# <a name="query-datasets"></a>Set di dati di query
Per cercare record specifici in un set di dati, usare il `FindBy` Metodo sulla DataTable, scrivere un'istruzione foreach personalizzata per eseguire il ciclo della raccolta Rows della tabella o usare [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Distinzione maiuscole/minuscole DataSet
All'interno di un set di dati, i nomi delle tabelle e delle colonne non fanno distinzione tra maiuscole e minuscole per impostazione predefinita, ovvero una tabella in un set di dati denominato "Customers" può essere definita anche "Customers". Corrisponde alle convenzioni di denominazione in molti database, tra cui SQL Server. In SQL Server, il comportamento predefinito è che i nomi degli elementi dati non possono essere distinti solo per caso.

> [!NOTE]
> A differenza dei set di dati, i documenti XML fanno distinzione tra maiuscole e minuscole, pertanto i nomi degli elementi dati definiti negli schemi fanno distinzione tra maiuscole e minuscole. Il protocollo schema consente, ad esempio, allo schema di definire una tabella denominata "Customers" e una tabella diversa denominata "Customers". Questo può causare conflitti di nomi quando uno schema che contiene elementi che differiscono solo per caso viene usato per generare una classe DataSet.

La distinzione tra maiuscole e minuscole, tuttavia, può essere un fattore determinante per interpretare i dati all'interno del DataSet. Se ad esempio si filtrano i dati in una tabella del set di dati, i criteri di ricerca potrebbero restituire risultati diversi a seconda che il confronto richieda la distinzione tra maiuscole e minuscole. È possibile controllare la distinzione tra maiuscole e minuscole del filtro, della ricerca e dell'ordinamento impostando la proprietà del set di dati <xref:System.Data.DataSet.CaseSensitive%2A> . Per impostazione predefinita, tutte le tabelle nel set di dati ereditano il valore di questa proprietà. È possibile eseguire l'override di questa proprietà per ogni singola tabella impostando la <xref:System.Data.DataTable.CaseSensitive%2A> proprietà della tabella.

## <a name="locate-a-specific-row-in-a-data-table"></a>Individuare una riga specifica in una tabella dati

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Per trovare una riga in un DataSet tipizzato con un valore di chiave primaria

- Per individuare una riga, chiamare il metodo fortemente tipizzato `FindBy` che utilizza la chiave primaria della tabella.

     Nell'esempio seguente la `CustomerID` colonna è la chiave primaria della `Customers` tabella. Questo significa che il `FindBy` metodo generato è `FindByCustomerID` . Nell'esempio viene illustrato come assegnare un oggetto specifico <xref:System.Data.DataRow> a una variabile utilizzando il `FindBy` metodo generato.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet18":::

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Per trovare una riga in un set di dati non tipizzato con un valore di chiave primaria

- Chiamare il <xref:System.Data.DataRowCollection.Find%2A> metodo di una <xref:System.Data.DataRowCollection> raccolta, passando la chiave primaria come parametro.

     Nell'esempio seguente viene illustrato come dichiarare una nuova riga denominata `foundRow` e assegnarle il valore restituito del <xref:System.Data.DataRowCollection.Find%2A> metodo. Se viene trovata la chiave primaria, il contenuto dell'indice di colonna 1 viene visualizzato in una finestra di messaggio.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet19":::

## <a name="find-rows-by-column-values"></a>Trova righe in base ai valori di colonna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Per trovare le righe in base ai valori in una colonna

- Le tabelle di dati vengono create con il <xref:System.Data.DataTable.Select%2A> metodo, che restituisce una matrice di oggetti <xref:System.Data.DataRow> in base all'espressione passata al <xref:System.Data.DataTable.Select%2A> metodo. Per ulteriori informazioni sulla creazione di espressioni valide, vedere la sezione "sintassi delle espressioni" della pagina relativa alla <xref:System.Data.DataColumn.Expression%2A> Proprietà.

     Nell'esempio seguente viene illustrato come utilizzare il <xref:System.Data.DataTable.Select%2A> metodo dell'oggetto <xref:System.Data.DataTable> per individuare righe specifiche.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet20":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet20":::

## <a name="access-related-records"></a>Accedere ai record correlati
Quando le tabelle in un set di dati sono correlate, un <xref:System.Data.DataRelation> oggetto può rendere disponibili i record correlati in un'altra tabella. Ad esempio, è possibile rendere disponibile un set di dati contenente `Customers` le `Orders` tabelle e.

È possibile utilizzare un <xref:System.Data.DataRelation> oggetto per individuare i record correlati chiamando il <xref:System.Data.DataRow.GetChildRows%2A> metodo di un oggetto <xref:System.Data.DataRow> nella tabella padre. Questo metodo restituisce una matrice di record figlio correlati. In alternativa, è possibile chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di un oggetto <xref:System.Data.DataRow> nella tabella figlio. Questo metodo restituisce un singolo oggetto <xref:System.Data.DataRow> dalla tabella padre.

In questa pagina vengono forniti esempi di utilizzo di DataSet tipizzati. Per informazioni sull'esplorazione delle relazioni nei set di dati non tipizzati, vedere esplorazione di oggetti [DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Se si lavora in una Windows Forms Application e si usano le funzionalità di data binding per visualizzare i dati, il form generato dalla finestra di progettazione potrebbe fornire una funzionalità sufficiente per l'applicazione. Per altre informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). In particolare, vedere [relazioni nei DataSet](relationships-in-datasets.md).

Negli esempi di codice seguenti viene illustrato come spostarsi in alto e in basso nelle relazioni nei dataset tipizzati. Negli esempi di codice vengono utilizzati i metodi tipizzati <xref:System.Data.DataRow> s ( `NorthwindDataSet.OrdersRow` ) e i FindBy *PrimaryKey* ( `FindByCustomerID` ) generati per individuare una riga desiderata e restituire i record correlati. Gli esempi vengono compilati ed eseguiti correttamente solo se si dispone di:

- Istanza di un set di dati denominato `NorthwindDataSet` con una `Customers` tabella.

- `Orders`Tabella.

- Relazione denominata che `FK_Orders_Customers` riguarda le due tabelle.

Inoltre, entrambe le tabelle devono essere riempite con i dati per i record da restituire.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Per restituire i record figlio di un record padre selezionato

- Chiamare il <xref:System.Data.DataRow.GetChildRows%2A> metodo di una `Customers` riga di dati specifica e restituire una matrice di righe dalla `Orders` tabella:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet6":::

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Per restituire il record padre di un record figlio selezionato

- Chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di una `Orders` riga di dati specifica e restituire una singola riga dalla `Customers` tabella:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Vedi anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
