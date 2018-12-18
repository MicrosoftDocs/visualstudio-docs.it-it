---
title: Associare gli oggetti in Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 64031303545f293d9274158eeb1527ba26676751
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bind-objects-in-visual-studio"></a>Associare gli oggetti in Visual Studio
Visual Studio fornisce gli strumenti di progettazione per l'utilizzo di oggetti personalizzati come origine dati nell'applicazione. Quando si desidera archiviare i dati da un database in un oggetto che associa controlli dell'interfaccia utente, l'approccio consigliato è usare Entity Framework per generare le classi. Entity Framework genera automaticamente tutti i codice boilerplate, rilevamento delle modifiche che significa che tutte le modifiche agli oggetti locali vengono rese automaticamente persistenti nel database quando si chiama AcceptChanges sull'oggetto DbSet. Per ulteriori informazioni, vedere [documentazione di Entity Framework](https://ef.readthedocs.org/en/latest/).  
  
> [!TIP]
>  Gli approcci per l'associazione di oggetti in questo articolo devono essere considerati solo se l'applicazione è già basato su set di dati. Questi approcci possono essere utilizzati anche se si ha già familiarità con i set di dati e i dati da elaborare sono tabulare e non è troppo complessa o troppo grande. Per un esempio ancora più semplice, che include il caricamento dei dati direttamente negli oggetti utilizzando un oggetto DataReader e aggiornare manualmente l'interfaccia utente senza l'associazione dati, vedere [creare un'applicazione dati semplice tramite ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
## <a name="object-requirements"></a>Requisiti di oggetto  
 L'unico requisito per gli oggetti personalizzati funzionare con i dati, strumenti di progettazione in Visual Studio è che l'oggetto è necessario selezionare almeno una proprietà pubblica.  
  
 In genere, gli oggetti personalizzati non richiedono le interfacce specifiche, costruttori o attributi a fungere da origine dati per un'applicazione. Tuttavia, se si desidera trascinare l'oggetto dal **origini dati** finestra all'area di progettazione per creare un controllo con associazione a dati, e se l'oggetto implementa il <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaccia, l'oggetto deve contenere un valore predefinito costruttore. In caso contrario, Visual Studio non è possibile creare un'istanza dell'oggetto origine dati e viene visualizzato un errore quando si trascina l'elemento nell'area di progettazione.  
  
## <a name="examples-of-using-custom-objects-as-data-sources"></a>Esempi di utilizzo di oggetti personalizzati come origini dati  
 Esistono moltissimi modi per implementare la logica dell'applicazione quando si utilizzano oggetti come origine dati, per SQL database vi sono alcune operazioni standard che possono essere semplificate tramite gli oggetti TableAdapter generati Visual Studio. Questa pagina viene illustrato come implementare questi processi standard utilizzando TableAdapters.It non è come guida per la creazione di oggetti personalizzati. Ad esempio, verranno in genere eseguite le seguenti operazioni standard indipendentemente dall'implementazione specifica di oggetti o logica dell'applicazione:  
  
-   Il caricamento dei dati in oggetti (in genere da un database).  
  
-   Creazione di una raccolta di oggetti tipizzata.  
  
-   Aggiunta e rimozione di oggetti da una raccolta.  
  
-   Visualizzazione di dati dell'oggetto agli utenti in un form.  
  
-   La modifica o modifica i dati in un oggetto.  
  
-   Salvataggio dei dati dagli oggetti nel database.   
  
### <a name="load-data-into-objects"></a>Caricare i dati in oggetti  
 Per questo esempio, si caricano dati in oggetti utilizzando gli oggetti TableAdapter. Per impostazione predefinita, vengono creati gli oggetti TableAdapter con due tipi di metodi per recupero i dati da un database e popolano le tabelle di dati.  
  
-   Il `TableAdapter.Fill` metodo compila una tabella dati esistente con i dati restituiti.  
  
-   Il `TableAdapter.GetData` metodo restituisce una nuova tabella dati popolata con i dati.  
  
 Per caricare gli oggetti personalizzati con i dati in modo semplice consiste nel chiamare il `TableAdapter.GetData` metodo, scorrere la raccolta di righe della tabella di dati restituiti e popolare ciascun oggetto con i valori in ogni riga. È possibile creare un `GetData` metodo che restituisce una tabella dati compilata per le query aggiunte a un oggetto TableAdapter.  
  
> [!NOTE]
>  Visual Studio i nomi di query del TableAdapter `Fill` e `GetData` per impostazione predefinita, ma tali nomi possono essere modificati a qualsiasi nome di metodo valido.  
  
 Nell'esempio seguente viene illustrato come scorrere le righe in una tabella dati e popola un oggetto con i dati:  
  
 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### <a name="create-a-typed-collection-of-objects"></a>Creare una raccolta tipizzata di oggetti  
 È possibile creare classi di raccolta per gli oggetti o utilizzare le raccolte tipizzate che sono fornite automaticamente dal [BindingSource (componente)](/dotnet/framework/winforms/controls/bindingsource-component).  
  
 Quando si crea una classe di raccolta personalizzato per gli oggetti, è consigliabile che si eredita da <xref:System.ComponentModel.BindingList%601>. Questa classe generica fornisce funzionalità per amministrare la raccolta, nonché la possibilità di generare eventi che inviano notifiche all'infrastruttura di data binding in Windows Form.  
  
 La raccolta generata automaticamente nel <xref:System.Windows.Forms.BindingSource> utilizza un <xref:System.ComponentModel.BindingList%601> per la relativa raccolta tipizzata. Se l'applicazione richiede funzionalità aggiuntive, è possibile gestire l'insieme all'interno di <xref:System.Windows.Forms.BindingSource>. Per ulteriori informazioni, vedere il <xref:System.Windows.Forms.BindingSource.List%2A> proprietà la <xref:System.Windows.Forms.BindingSource> classe.  
  
> [!NOTE]
>  Se la raccolta richiede funzionalità non fornite dall'implementazione di base di <xref:System.ComponentModel.BindingList%601>, è necessario creare una raccolta personalizzata, è possibile aggiungere alla classe, in base alle esigenze.  
  
 Il codice seguente viene illustrato come creare la classe per una raccolta fortemente tipizzata di `Order` oggetti:  
  
 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### <a name="add-objects-to-a-collection"></a>Aggiungere gli oggetti a una raccolta  
 Per aggiungere oggetti a una raccolta, chiamare il `Add` metodo della classe di raccolta personalizzato oppure del <xref:System.Windows.Forms.BindingSource>.  
  
 
> [!NOTE]
>  Il `Add` metodo viene fornito automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601>.  
  
 Il codice seguente viene illustrato come aggiungere oggetti alla raccolta tipizzata in una <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 Il codice seguente viene illustrato come aggiungere oggetti a una raccolta tipizzata che eredita da <xref:System.ComponentModel.BindingList%601>:  
  
> [!NOTE]
>  In questo esempio il `Orders` raccolta è una proprietà del `Customer` oggetto.  
  
 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### <a name="remove-objects-from-a-collection"></a>Rimuovere gli oggetti da una raccolta  
 Rimuovere gli oggetti da una raccolta chiamando il `Remove` o `RemoveAt` metodo della classe di raccolta personalizzato oppure di <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Il `Remove` e `RemoveAt` metodi vengono forniti automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601>.  
  
 Il codice seguente viene illustrato come individuare e rimuovere gli oggetti dalla raccolta tipizzata in una <xref:System.Windows.Forms.BindingSource> con il <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metodo:  
  
 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### <a name="display-object-data-to-users"></a>Visualizzare i dati dell'oggetto per gli utenti  
 Per visualizzare i dati negli oggetti agli utenti, creare un'origine dati di oggetti utilizzando il **configurazione guidata origine dati** procedura guidata e quindi trascinare l'intero oggetto o le singole proprietà nel form dal **origini dati**finestra.  
  
### <a name="modify-the-data-in-objects"></a>Modificare i dati negli oggetti  
 Per modificare i dati negli oggetti personalizzati che sono con associazione dati a controlli Windows Form, è sufficiente modificare i dati nel controllo associato (o direttamente nella proprietà dell'oggetto). Architettura di associazione dati aggiorna i dati nell'oggetto.  
  
 Se l'applicazione richiede il rilevamento delle modifiche e il rollback delle modifiche proposte ai valori originali, è necessario implementare questa funzionalità nel modello a oggetti. Per esempi di come le tabelle di dati tenere traccia delle modifiche proposte, vedere <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, e <xref:System.Data.DataTable.GetChanges%2A>.  
  
### <a name="save-data-in-objects-back-to-the-database"></a>Salvare i dati negli oggetti nel database  
 Salvare i dati del database passando i valori dall'oggetto ai metodi DBDirect di TableAdapter.  
  
 Visual Studio crea DBDirect (metodi) che possono essere eseguiti direttamente nel database. Questi metodi non richiedono oggetti DataSet o DataTable.  
  
|Metodo DBDirect di TableAdapter|Descrizione|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Aggiunge nuovi record in un database, che consente di passare i valori delle singole colonne come parametri di metodo.|  
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il metodo Update accetta valori di colonna originali e quelli nuovi come parametri di metodo. I valori originali vengono utilizzati per individuare il record originale e i nuovi valori vengono utilizzati per aggiornare il record.<br /><br /> Il `TableAdapter.Update` metodo viene utilizzato anche per risolvere le modifiche in un set di dati al database, tramite l'aggiunta di un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matrice di <xref:System.Data.DataRow>come parametri del metodo.|  
|`TableAdapter.Delete`|Elimina i record dal database in base ai valori di colonna originale passati come parametri del metodo esistenti.|  
  
 Per salvare i dati da una raccolta di oggetti, scorrere la raccolta di oggetti (ad esempio, utilizzando un ciclo for next). Inviare i valori per ogni oggetto al database utilizzando i metodi DBDirect di TableAdapter.  
  
 Nell'esempio seguente viene illustrato come utilizzare il `TableAdapter.Insert` metodo DBDirect per aggiungere un nuovo cliente direttamente nel database:  
  
 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)