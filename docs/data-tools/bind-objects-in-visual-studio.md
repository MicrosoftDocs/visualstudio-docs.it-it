---
title: Oggetti personalizzati di associazione dati
description: Associare oggetti come origini dati in Visual Studio. Usare gli strumenti in fase di progettazione per lavorare con oggetti personalizzati come origine dati nell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 140700615759404f02109c4506f4c27d083a74b1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215539"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Associare oggetti come origini dati in Visual Studio

Visual Studio offre strumenti in fase di progettazione per l'utilizzo di oggetti personalizzati come origine dati nell'applicazione. Quando si desidera archiviare i dati da un database in un oggetto associato ai controlli dell'interfaccia utente, l'approccio consigliato consiste nell'utilizzare Entity Framework per generare la classe o le classi. Entity Framework genera automaticamente tutto il codice di rilevamento delle modifiche standard, il che significa che tutte le modifiche apportate agli oggetti locali vengono rese automaticamente permanente nel database quando si chiama AcceptChanges nell'oggetto DbSet. Per ulteriori informazioni, vedere [Entity Framework documentazione](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Gli approcci all'associazione di oggetti in questo articolo devono essere considerati solo se l'applicazione è già basata sui set di impostazioni. È anche possibile usare questi approcci se si ha già familiarità con i set di dati e i dati che verranno elaborati sono tabulari e non troppo complessi o troppo grandi. Per un esempio ancora più semplice, che implica il caricamento dei dati direttamente negli oggetti usando un DataReader e l'aggiornamento manuale dell'interfaccia utente senza data binding, vedere [creare un'applicazione dati semplice usando ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisiti per gli oggetti

L'unico requisito per usare gli oggetti personalizzati con gli strumenti di progettazione dei dati in Visual Studio è che l'oggetto necessita almeno di una proprietà pubblica.

In genere, gli oggetti personalizzati non richiedono interfacce, costruttori o attributi specifici che fungano da origine dati per un'applicazione. Tuttavia, se si desidera trascinare l'oggetto dalla finestra **origini dati** in un'area di progettazione per creare un controllo con associazione a dati e se l'oggetto implementa l' <xref:System.ComponentModel.ITypedList> interfaccia o <xref:System.ComponentModel.IListSource> , l'oggetto deve disporre di un costruttore predefinito. In caso contrario, Visual Studio non è in grado di creare un'istanza dell'oggetto origine dati e viene visualizzato un errore quando si trascina l'elemento nell'area di progettazione.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Esempi di utilizzo di oggetti personalizzati come origini dati

Sebbene esistano innumerevoli modi per implementare la logica dell'applicazione quando si utilizzano oggetti come origine dati, per i database SQL sono disponibili alcune operazioni standard che possono essere semplificate tramite gli oggetti TableAdapter generati da Visual Studio. In questa pagina viene illustrato come implementare questi processi standard utilizzando oggetti TableAdapter. Non viene utilizzato come guida per la creazione di oggetti personalizzati. Ad esempio, si eseguono in genere le operazioni standard seguenti indipendentemente dall'implementazione specifica degli oggetti o dalla logica dell'applicazione:

- Caricamento dei dati in oggetti, in genere da un database.

- Creazione di una raccolta tipizzata di oggetti.

- Aggiunta e rimozione di oggetti da una raccolta.

- Visualizzazione dei dati oggetto per gli utenti in un form.

- Modifica o modifica dei dati in un oggetto.

- Salvataggio di dati dagli oggetti di nuovo nel database.

### <a name="load-data-into-objects"></a>Caricare i dati in oggetti

Per questo esempio, si caricano i dati negli oggetti usando TableAdapter. Per impostazione predefinita, gli oggetti TableAdapter vengono creati con due tipi di metodi che recuperano dati da un database e popolano le tabelle di dati.

- Il `TableAdapter.Fill` metodo compila una tabella dati esistente con i dati restituiti.

- Il `TableAdapter.GetData` metodo restituisce una nuova tabella dati popolata con i dati.

Il modo più semplice per caricare gli oggetti personalizzati con dati consiste nel chiamare il `TableAdapter.GetData` metodo, eseguire il ciclo della raccolta di righe nella tabella dati restituita e popolare ogni oggetto con i valori in ogni riga. È possibile creare un `GetData` metodo che restituisca una tabella dati popolata per qualsiasi query aggiunta a un TableAdapter.

> [!NOTE]
> Visual Studio denomina le query TableAdapter `Fill` e per `GetData` impostazione predefinita, ma è possibile modificare tali nomi in qualsiasi nome di metodo valido.

Nell'esempio seguente viene illustrato come eseguire il ciclo delle righe in una tabella di dati e compilare un oggetto con i dati:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb" id="Snippet4":::

### <a name="create-a-typed-collection-of-objects"></a>Creare una raccolta tipizzata di oggetti

È possibile creare classi di raccolte per gli oggetti oppure utilizzare le raccolte tipizzate fornite automaticamente dal [componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Quando si crea una classe di raccolta personalizzata per gli oggetti, è consigliabile ereditare da <xref:System.ComponentModel.BindingList%601> . Questa classe generica fornisce funzionalità per l'amministrazione della raccolta, nonché la possibilità di generare eventi che inviano notifiche all'infrastruttura di associazione dati in Windows Form.

La raccolta generata automaticamente in <xref:System.Windows.Forms.BindingSource> Usa un oggetto <xref:System.ComponentModel.BindingList%601> per la raccolta tipizzata. Se l'applicazione non richiede funzionalità aggiuntive, è possibile gestire la raccolta all'interno di <xref:System.Windows.Forms.BindingSource> . Per ulteriori informazioni, vedere la <xref:System.Windows.Forms.BindingSource.List%2A> proprietà della <xref:System.Windows.Forms.BindingSource> classe.

> [!NOTE]
> Se per la raccolta è richiesta la funzionalità non fornita dall'implementazione di base di <xref:System.ComponentModel.BindingList%601> , è necessario creare una raccolta personalizzata in modo che sia possibile aggiungerla alla classe in base alle esigenze.

Nel codice seguente viene illustrato come creare la classe per una raccolta fortemente tipizzata di `Order` oggetti:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet8":::

### <a name="add-objects-to-a-collection"></a>Aggiungere oggetti a una raccolta

Per aggiungere oggetti a una raccolta, chiamare il `Add` metodo della classe di raccolta personalizzata o di <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> Il `Add` metodo viene fornito automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601> .

Nel codice seguente viene illustrato come aggiungere oggetti alla raccolta tipizzata in un oggetto <xref:System.Windows.Forms.BindingSource> :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet5":::

Nel codice seguente viene illustrato come aggiungere oggetti a una raccolta tipizzata che eredita da <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> In questo esempio, la `Orders` raccolta è una proprietà dell' `Customer` oggetto.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet6":::

### <a name="remove-objects-from-a-collection"></a>Rimuovere oggetti da una raccolta

Per rimuovere oggetti da una raccolta, chiamare il `Remove` `RemoveAt` metodo o della classe di raccolta personalizzata o di <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> I `Remove` `RemoveAt` metodi e vengono forniti automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601> .

Nel codice seguente viene illustrato come individuare e rimuovere oggetti dalla raccolta tipizzata in un oggetto <xref:System.Windows.Forms.BindingSource> con il <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> Metodo:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet7":::

### <a name="display-object-data-to-users"></a>Visualizza dati oggetto agli utenti

Per visualizzare i dati negli oggetti per gli utenti, creare un'origine dati oggetto utilizzando la **Configurazione guidata origine dati** , quindi trascinare l'intero oggetto o le singole proprietà nel form dalla finestra **origini dati** .

### <a name="modify-the-data-in-objects"></a>Modificare i dati negli oggetti

Per modificare i dati in oggetti personalizzati che sono associati a dati a controlli di Windows Form, è sufficiente modificare i dati nel controllo associato (o direttamente nelle proprietà dell'oggetto). L'architettura di data binding aggiorna i dati nell'oggetto.

Se l'applicazione richiede il rilevamento delle modifiche e il rollback delle modifiche proposte ai valori originali, è necessario implementare questa funzionalità nel modello a oggetti. Per esempi di come le tabelle dati tengono traccia delle modifiche proposte, vedere <xref:System.Data.DataRowState> , <xref:System.Data.DataSet.HasChanges%2A> e <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Salvare i dati negli oggetti di nuovo nel database

Salvare nuovamente i dati nel database passando i valori dall'oggetto ai metodi DBDirect del TableAdapter.

Visual Studio crea metodi DBDirect che possono essere eseguiti direttamente sul database. Questi metodi non richiedono oggetti DataSet o DataTable.

|Metodo DBDirect di TableAdapter|Descrizione|
| - |-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database, consentendo di passare i singoli valori di colonna come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il metodo Update accetta i valori di colonna originali e nuovi come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare il record.<br /><br /> Il `TableAdapter.Update` metodo viene inoltre usato per riconciliare le modifiche in un set di dati nel database, accettando una <xref:System.Data.DataSet> matrice,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> o di <xref:System.Data.DataRow> s come parametri del metodo.|
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri del metodo.|

Per salvare i dati da una raccolta di oggetti, eseguire il ciclo della raccolta di oggetti, ad esempio usando un ciclo for-Next. Inviare i valori per ogni oggetto al database usando i metodi DBDirect del TableAdapter.

Nell'esempio seguente viene illustrato come utilizzare il `TableAdapter.Insert` metodo DBDirect per aggiungere un nuovo cliente direttamente nel database:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
