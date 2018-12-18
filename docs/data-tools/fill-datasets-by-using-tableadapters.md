---
title: Compilare i set di dati utilizzando gli oggetti TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 49f3aad9adf319c09097324a6c40a4aa7b8f6692
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="fill-datasets-by-using-tableadapters"></a>Compilare i set di dati utilizzando gli oggetti TableAdapter
Un componente TableAdapter viene compilato un set di dati con i dati dal database, in base a uno o più query o stored procedure specificate. Inoltre è possibile eseguire gli oggetti TableAdapter aggiunge, aggiornamenti ed eliminazioni per rendere permanenti le modifiche apportate al set di dati nel database. È inoltre possibile emettere comandi globali che sono correlati a qualsiasi tabella specifica.

> [!NOTE]
>  Gli oggetti TableAdapter generati dalle finestre di progettazione di Visual Studio. Se si creano set di dati a livello di codice, quindi utilizzare DataAdapter, ovvero una classe .NET Framework.

 Per informazioni dettagliate sulle operazioni del TableAdapter, è possibile passare direttamente a uno degli argomenti seguenti:

|Argomento|Descrizione|
|-----------|-----------------|
|[Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Come utilizzare le finestre di progettazione per creare e configurare gli oggetti TableAdapter|
|[Creare query TableAdapter con parametri](../data-tools/create-parameterized-tableadapter-queries.md)|Come consentire agli utenti di fornire argomenti di procedure TableAdapter o alle query|
|[Accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Come utilizzare i metodi Dbdirect di TableAdapter|
|[Disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Come utilizzare i vincoli di chiave esterna quando l'aggiornamento dei dati|
|[Come estendere la funzionalità di un oggetto TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Come aggiungere codice personalizzato per gli oggetti TableAdapter|
|[Leggere dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md)|Utilizzo XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Panoramica degli oggetti TableAdapter
 Gli oggetti TableAdapter sono componenti generato da progettazione che si connettono a un database, eseguire query o stored procedure e compilare il DataTable con i dati restituiti. Gli oggetti TableAdapter anche inviare dati aggiornati dall'applicazione al database. È possibile eseguire il numero di query su un oggetto TableAdapter a condizione che restituiscono dati conformi allo schema della tabella a cui è associato l'oggetto TableAdapter. Il diagramma seguente illustra come gli oggetti TableAdapter interagire con i database e altri oggetti in memoria:

 ![Flusso di dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")

 Mentre gli oggetti TableAdapter sono progettate con la **Progettazione Dataset**, le classi TableAdapter non vengono generate come classi annidate di <xref:System.Data.DataSet>. Si trovano in spazi dei nomi distinti che sono specifiche per ogni set di dati. Ad esempio, se si dispone di un set di dati denominato `NorthwindDataSet`, gli oggetti TableAdapter associati <xref:System.Data.DataTable>s nel `NorthwindDataSet` verrebbero il `NorthwindDataSetTableAdapters` dello spazio dei nomi. Per accedere a un determinato TableAdapter a livello di codice, è necessario dichiarare una nuova istanza dell'oggetto TableAdapter. Ad esempio:

 [!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
 [!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Associati a uno schema di DataTable
 Quando si crea un oggetto TableAdapter, usare la query iniziale o stored procedure per definire lo schema dell'oggetto TableAdapter associato <xref:System.Data.DataTable>. Si esegue questa query iniziale o stored procedure tramite la chiamata dell'oggetto TableAdapter `Fill` metodo (che determina il riempimento dell'oggetto TableAdapter associato <xref:System.Data.DataTable>). Eventuali modifiche apportate alla query principale dell'oggetto TableAdapter vengono riflesse nello schema della tabella dati associata. Ad esempio, la rimozione di una colonna dalla query principale rimuove la colonna dalla tabella di dati associato. Se le query del TableAdapter utilizzano istruzioni SQL che restituiscono colonne che non sono presenti nella query principale, la finestra di progettazione viene effettuato un tentativo di sincronizzare le modifiche di colonna tra la query principale e le query aggiuntive.

## <a name="tableadapter-update-commands"></a>Comandi di aggiornamento di TableAdapter
 La funzionalità di aggiornamento di un oggetto TableAdapter è dipendente dalla quantità di informazioni è disponibile la query principale della procedura guidata TableAdapter. Ad esempio, gli oggetti TableAdapter che sono configurati per recuperare valori da più tabelle (join), valori scalari, viste o i risultati delle funzioni di aggregazione non vengono creati inizialmente con la possibilità di inviare aggiornamenti al database sottostante. Tuttavia, è possibile configurare manualmente i comandi INSERT, UPDATE e DELETE di **proprietà** finestra.

## <a name="tableadapter-queries"></a>TableAdapter (query)
 ![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")

 Gli oggetti TableAdapter può contenere più query per compilare le tabelle dati associate. È possibile definire tutte le query per un oggetto TableAdapter richieste dall'applicazione, purché ogni query restituisce dati conformi allo stesso schema della tabella dati associata. Questa funzionalità consente a un oggetto TableAdapter caricare i risultati diversi in base a diversi criteri.

 Ad esempio, se l'applicazione contiene una tabella con i nomi dei clienti, è possibile creare una query che riempie la tabella con ogni nome di cliente che inizia con una determinata lettera e l'altro che riempie la tabella con tutti i clienti che si trovano nello stesso stato. Per riempire un `Customers` tabella con i clienti in uno stato specifico, è possibile creare un `FillByState` query che accetta un parametro per il valore di stato come segue: `SELECT * FROM Customers WHERE State = @State`. Eseguire la query chiamando la `FillByState` metodo e passando il valore del parametro come segue: `CustomerTableAdapter.FillByState("WA")`.

 Oltre ad aggiungere le query che restituiscono dati dello stesso schema della tabella di dati dell'oggetto TableAdapter, è possibile aggiungere le query che restituiscono valori scalari di (singolo). Ad esempio, una query che restituisce un conteggio di clienti (`SELECT Count(*) From Customers`) è valido per un `CustomersTableAdapter,` anche se i dati restituiti non sono conformi allo schema della tabella.

## <a name="clearbeforefill-property"></a>Proprietà ClearBeforeFill
 Per impostazione predefinita, ogni volta che si esegue una query per riempire dati tabella un oggetto TableAdapter, i dati esistenti viene cancellati e vengono caricati solo i risultati della query nella tabella. Impostare il TableAdapter `ClearBeforeFill` proprietà `false` se si desidera aggiungere o unire i dati restituiti da una query per i dati esistenti in una tabella dati. Indipendentemente dal fatto se si cancella i dati, è necessario inviare in modo esplicito gli aggiornamenti al database, se si desidera renderle persistenti. È importante salvare eventuali modifiche ai dati nella tabella prima di eseguire un'altra query che riempie la tabella. Per ulteriori informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Ereditarietà di TableAdapter
 Oggetti TableAdapter estendere la funzionalità di adattatori di dati standard incapsulando configurato <xref:System.Data.Common.DataAdapter> classe. Per impostazione predefinita, l'oggetto TableAdapter eredita il <xref:System.ComponentModel.Component> classe e non può essere convertito il <xref:System.Data.Common.DataAdapter> classe. Cast di un oggetto TableAdapter per la <xref:System.Data.Common.DataAdapter> classe risultati in un <xref:System.InvalidCastException> errore. Per modificare la classe di base di un oggetto TableAdapter, è possibile specificare una classe che deriva da <xref:System.ComponentModel.Component> nel **classe di Base** proprietà dell'oggetto TableAdapter nel **Progettazione Dataset**.

## <a name="tableadapter-methods-and-properties"></a>Proprietà e metodi di TableAdapter
 La classe TableAdapter non è in parte il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Ciò significa che è possibile cercarla nella documentazione o **Visualizzatore oggetti**. Viene creato in fase di progettazione quando si utilizza una delle procedure guidate indicate in precedenza. Il nome assegnato a un oggetto TableAdapter quando si crea è basato sul nome della tabella in uso. Ad esempio, quando si crea un oggetto TableAdapter in base a una tabella in un database denominato `Orders`, dell'oggetto TableAdapter denominato `OrdersTableAdapter`. Il nome della classe dell'oggetto TableAdapter può essere modificato utilizzando il **nome** proprietà il **Progettazione Dataset**.

 Di seguito sono utilizzati i metodi e alle proprietà degli oggetti TableAdapter:

|Member|Descrizione|
|------------|-----------------|
|`TableAdapter.Fill`|Popola una tabella dati associata dell'oggetto TableAdapter con i risultati del comando SELECT dell'oggetto TableAdapter.|
|`TableAdapter.Update`|Invia modifiche al database e restituisce un intero che rappresenta il numero di righe interessate dall'aggiornamento. Per ulteriori informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Restituisce un nuovo <xref:System.Data.DataTable> che viene riempita con dati.|
|`TableAdapter.Insert`|Crea una nuova riga nella tabella dati. Per ulteriori informazioni, vedere [inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Determina se una tabella di dati viene svuotata prima di chiamare uno del `Fill` metodi.|

## <a name="tableadapter-update-method"></a>Metodo update di TableAdapter
 Gli oggetti TableAdapter utilizzare i comandi di dati per leggere e scrivere dal database. Iniziale dell'oggetto TableAdapter `Fill` query (principale) viene utilizzata come base per creare lo schema della tabella di dati associato, nonché il `InsertCommand`, `UpdateCommand`, e `DeleteCommand` i comandi che sono associati il `TableAdapter.Update` (metodo). La chiamata a un oggetto TableAdapter `Update` esecuzione del metodo le istruzioni che sono state create al TableAdapter è stata originariamente configurata, non una delle altre query che è stato aggiunto con il **configurazione guidata Query TableAdapter**.

 Quando si utilizza un oggetto TableAdapter, esegue in modo efficace le stesse operazioni con i comandi eseguibili in genere. Ad esempio, quando si chiama l'adapter `Fill` (metodo), l'adapter viene eseguito il comando di dati relativo `SelectCommand` proprietà e utilizza un lettore di dati (ad esempio, <xref:System.Data.SqlClient.SqlDataReader>) per caricare il set dei risultati nella tabella di dati. Analogamente, quando si chiama l'adapter `Update` (metodo), viene eseguito il comando appropriato (nel `UpdateCommand`, `InsertCommand`, e `DeleteCommand` proprietà) per ciascun record nella tabella di dati modificato.

> [!NOTE]
>  Se non sono sufficienti informazioni della query principale, il `InsertCommand`, `UpdateCommand`, e `DeleteCommand` i comandi vengono creati per impostazione predefinita, quando viene generato il TableAdapter. Se la query TableAdapter principale è maggiore rispetto a un'istruzione SELECT singola tabella, è possibile la finestra di progettazione non sarà in grado di generare `InsertCommand`, `UpdateCommand`, e `DeleteCommand`. Questi comandi non vengono generati, si potrebbe venire visualizzato un errore durante l'esecuzione di `TableAdapter.Update` metodo.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods
 Oltre a `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, vengono creati gli oggetti TableAdapter con metodi che possono essere eseguiti direttamente nel database. Questi metodi (`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`) può essere chiamato direttamente per la modifica di dati nel database. Ciò significa che è possibile chiamare questi metodi singoli dal codice anziché chiamare `TableAdapter.Update` per la gestione di inserimenti, aggiornamenti ed eliminazioni in sospeso per la tabella di dati associati.

 Se non si desidera creare questi metodi diretti, impostare il TableAdapter **GenerateDbDirectMethods** proprietà `false` (nel **proprietà** finestra). Le query aggiuntive che vengono aggiunti all'oggetto TableAdapter sono autonome, ovvero non generano questi metodi.

## <a name="tableadapter-support-for-nullable-types"></a>Supporto dei TableAdapter per i tipi nullable
 Gli oggetti TableAdapter supporta i tipi nullable `Nullable(Of T)` e `T?`. Per altre informazioni sui tipi nullable in Visual Basic, vedere [Tipi di valori Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Per ulteriori informazioni sui tipi nullable in c#, vedere [utilizzando i tipi Nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Riferimento di TableAdapterManager
 Per impostazione predefinita, un `TableAdapterManager` classe viene generata quando si crea un set di dati che contiene tabelle correlate. Per impedire la generazione della classe, modificare il valore della `Hierarchical Update` proprietà del set di dati su false. Quando si trascina una tabella che dispone di una relazione nell'area di progettazione di un Windows Form o una pagina WPF, Visual Studio dichiara una variabile membro della classe. Se non si utilizza l'associazione dati, è necessario dichiarare manualmente la variabile.

 Il `TableAdapterManager` classe non è in parte il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Pertanto, è possibile cercarla nella documentazione. Viene creato in fase di progettazione come parte del processo di creazione di set di dati.

 Di seguito sono i metodi usati di frequente e le proprietà di `TableAdapterManager` classe:

|Member|Descrizione|
|------------|-----------------|
|Metodo `UpdateAll`|Salva tutti i dati da tutte le tabelle di dati.|
|Proprietà `BackUpDataSetBeforeUpdate`|Determina se creare una copia di backup del set di dati prima di eseguire il `TableAdapterManager.UpdateAll` metodo. Valore booleano.|
|*tableName* `TableAdapter` proprietà|Rappresenta un `TableAdapter`. Generato `TableAdapterManager` contiene una proprietà per ogni `TableAdapter` gestisce. Ad esempio, un set di dati con una tabella Customers e Orders viene generato con un `TableAdapterManager` contenente `CustomersTableAdapter` e `OrdersTableAdapter` proprietà.|
|Proprietà `UpdateOrder`|Controlla l'ordine dei comandi di eliminazione, aggiornamento e inserimento singolo. Impostare questa proprietà su uno dei valori di `TableAdapterManager.UpdateOrderOption` enumerazione.<br /><br /> Per impostazione predefinita, il `UpdateOrder` è impostato su **InsertUpdateDelete**. Ciò significa che inserisce, quindi aggiorna e quindi Elimina vengono eseguite per tutte le tabelle nel set di dati.|

## <a name="security"></a>Sicurezza
Quando si utilizzano i comandi di dati con una proprietà CommandType è impostata su <xref:System.Data.CommandType.Text>, attentamente controllare le informazioni inviate da un client prima di passarlo al database. Gli utenti malintenzionati potrebbero tentare di inviare (introdurre) istruzioni SQL modificate o aggiuntive nel tentativo di accesso non autorizzato o danneggiare il database. Prima di trasferire l'input dell'utente a un database, verificare sempre che le informazioni non valide. Una procedura consigliata consiste nell'utilizzare sempre query con parametri o stored procedure quando possibile.

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati](../data-tools/dataset-tools-in-visual-studio.md)