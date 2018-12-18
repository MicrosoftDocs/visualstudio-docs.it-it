---
title: Set di dati di query | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: f25507493237ba54c9d6820500706d06d4bf7710
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="query-datasets"></a>Set di dati di query
Per cercare un record specifico in un set di dati, utilizzare il metodo FindBy in DataTable, scrivere la propria istruzione foreach per eseguire un ciclo in una raccolta di righe della tabella o utilizzare [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
## <a name="dataset-case-sensitivity"></a>Set di dati distinzione maiuscole/minuscole  
All'interno di un set di dati, i nomi di tabella e colonna sono tra maiuscole e minuscole per impostazione predefinita, vale a dire, una tabella in un set di dati denominato "Customers" può anche essere indicata come "customers". Questo corrisponde le convenzioni di denominazione in numerosi database, incluso SQL Server. In SQL Server, il comportamento predefinito è che non è possibile distinguere i nomi degli elementi di dati solo dalle maiuscole o minuscole.  
  
> [!NOTE]
>  A differenza di set di dati, documenti XML tra maiuscole e minuscole, pertanto i nomi di elementi di dati definiti negli schemi di maiuscole e minuscole. Ad esempio, del protocollo, lo schema definire una tabella denominata "Customers" e una tabella diversa denominata "customers". Questo può causare conflitti di nome quando uno schema che contiene gli elementi che differiscono solo per i casi viene utilizzato per generare una classe dataset.  
  
Distinzione maiuscole/minuscole, tuttavia, è possibile influire sull'interpretazione dei dati all'interno del dataset. Ad esempio, se si filtrano i dati in una tabella di set di dati, i criteri di ricerca potrebbero restituire risultati diversi a seconda se il confronto tra maiuscole e minuscole. È possibile controllare la distinzione maiuscole/minuscole di filtro, la ricerca e ordinamento impostando il set di dati <xref:System.Data.DataSet.CaseSensitive%2A> proprietà. Per impostazione predefinita, tutte le tabelle nel set di dati ereditano il valore di questa proprietà. (È possibile eseguire l'override di questa proprietà per ogni tabella tramite l'impostazione della tabella <xref:System.Data.DataTable.CaseSensitive%2A> proprietà.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Individuare una riga specifica in una tabella di dati  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Per trovare una riga in un dataset tipizzato con un valore di chiave primaria  
  
-   Per individuare una riga, chiamare l'oggetto fortemente tipizzato `FindBy` metodo che usa una chiave primaria della tabella.  
  
     Nell'esempio seguente, il `CustomerID` colonna è la chiave primaria del `Customers` tabella. Ciò significa che il generato `FindBy` metodo `FindByCustomerID`. Nell'esempio viene illustrato come assegnare uno specifico <xref:System.Data.DataRow> a una variabile utilizzando generato `FindBy` metodo.  
  
     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Per trovare una riga in un dataset tipizzato con un valore di chiave primaria  
  
-   Chiamare il <xref:System.Data.DataRowCollection.Find%2A> metodo di un <xref:System.Data.DataRowCollection> insieme, passando la chiave primaria come parametro.  
  
     Nell'esempio seguente viene illustrato come dichiarare una nuova riga denominata `foundRow` e assegnarvi il valore restituito del <xref:System.Data.DataRowCollection.Find%2A> metodo. Se viene trovata la chiave primaria, il contenuto dell'indice di colonna 1 viene visualizzato in una finestra di messaggio.  
  
     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]  
  
## <a name="find-rows-by-column-values"></a>Trovare le righe dai valori di colonna  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Per trovare le righe in base ai valori in qualsiasi colonna  
  
-   Le tabelle di dati vengono create con la <xref:System.Data.DataTable.Select%2A> metodo, che restituisce una matrice di <xref:System.Data.DataRow>s basato sull'espressione passata al <xref:System.Data.DataTable.Select%2A> metodo. Per ulteriori informazioni sulla creazione di espressioni valide, vedere la sezione "Sintassi delle espressioni" della pagina <xref:System.Data.DataColumn.Expression%2A> proprietà.  
  
     Nell'esempio seguente viene illustrato come utilizzare il <xref:System.Data.DataTable.Select%2A> metodo il <xref:System.Data.DataTable> per individuare le righe specifiche.  
  
     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]  
  
## <a name="access-related-records"></a>Accesso per i record correlati.  
Quando le tabelle in un set di dati sono correlate, un <xref:System.Data.DataRelation> oggetto può rendere i record correlati disponibili in un'altra tabella. Ad esempio, un set di dati contenente `Customers` e `Orders` tabelle possono essere resi disponibili.  
  
È possibile utilizzare un <xref:System.Data.DataRelation> oggetto da individuare i record correlati chiamando il <xref:System.Data.DataRow.GetChildRows%2A> metodo di un <xref:System.Data.DataRow> nella tabella padre. Questo metodo restituisce una matrice di record figlio correlati. Oppure è possibile chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di un <xref:System.Data.DataRow> nella tabella figlio. Questo metodo restituisce un singolo <xref:System.Data.DataRow> dalla tabella padre.  
  
In questa pagina vengono forniti esempi di uso di dataset tipizzati. Per informazioni sull'esplorazione di relazioni nei dataset non tipizzati, vedere [esplorazione DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).  
  
> [!NOTE]
>  Se si lavora in un'applicazione Windows Form e usando le funzionalità di associazione dati per visualizzare i dati, generato da Progettazione form potrebbe forniscono le funzionalità necessarie per l'applicazione. Per ulteriori informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). In particolare, vedere [relazioni nei DataSet](relationships-in-datasets.md).  
  
Gli esempi di codice seguente viene illustrato come spostarsi su e giù relazioni nei dataset tipizzati. L'utilizzo di esempi di codice tipizzato <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) e il FindBy generato*PrimaryKey* (`FindByCustomerID`) per individuare una riga desiderata e restituire i record correlati. Gli esempi di compilare ed eseguire correttamente solo se è necessario:  
  
-   Un'istanza di un set di dati denominato `NorthwindDataSet` con un `Customers` tabella.  
  
-   Un `Orders` tabella.  
  
-   Una relazione denominata `FK_Orders_Customers`collega le due tabelle.  
  
Entrambe le tabelle è inoltre necessario da riempire di dati per tutti i record da restituire.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Per restituire i record di un record padre selezionato figlio  
  
-   Chiamare il <xref:System.Data.DataRow.GetChildRows%2A> metodo di uno specifico `Customers` dati di riga e una matrice di righe da restituire il `Orders` tabella:  
  
     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Per restituire il record padre di un record figlio selezionato  
  
-   Chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di uno specifico `Orders` riga di dati e restituire una singola riga dal `Customers` tabella:  
  
     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Vedere anche
[Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  