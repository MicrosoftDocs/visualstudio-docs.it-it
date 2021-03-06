---
title: Creare relazioni tra set di dati
description: Creare relazioni tra set di impostazioni in Visual Studio. Informazioni sugli oggetti e sui vincoli DataRelation. Creare manualmente una relazione dati in gestione DataSet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 92e1a03a9a72b550c77aa734c4a9ff2d0b184839
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866606"
---
# <a name="create-relationships-between-datasets"></a>Creare relazioni tra set di dati
I set di dati che contengono tabelle di dati correlate utilizzano <xref:System.Data.DataRelation> oggetti per rappresentare una relazione padre/figlio tra le tabelle e per restituire record correlati gli uni dagli altri. L'aggiunta di tabelle correlate ai set di dati tramite la **Configurazione guidata origine dati** o la **Progettazione DataSet** crea e configura automaticamente l' <xref:System.Data.DataRelation> oggetto.

L' <xref:System.Data.DataRelation> oggetto esegue due funzioni:

- Può rendere disponibili i record correlati a un record che si sta utilizzando. Fornisce record figlio se ci si trova in un record padre ( <xref:System.Data.DataRow.GetChildRows%2A> ) e in un record padre se si utilizza un record figlio ( <xref:System.Data.DataRow.GetParentRow%2A> ).

- Può applicare vincoli per l'integrità referenziale, ad esempio l'eliminazione di record figlio correlati quando si elimina un record padre.

È importante comprendere la differenza tra un join reale e la funzione di un <xref:System.Data.DataRelation> oggetto. In un join reale, i record vengono ricavati dalle tabelle padre e figlio e inseriti in un singolo recordset flat. Quando si utilizza un <xref:System.Data.DataRelation> oggetto, non viene creato alcun nuovo recordset. DataRelation rileva invece la relazione tra le tabelle e mantiene sincronizzati i record padre e figlio.

## <a name="datarelation-objects-and-constraints"></a>Oggetti DataRelation e vincoli
Un <xref:System.Data.DataRelation> oggetto viene usato anche per creare e applicare i vincoli seguenti:

- Vincolo UNIQUE, che garantisce che una colonna della tabella non contenga duplicati.

- Vincolo FOREIGN KEY, che può essere utilizzato per mantenere l'integrità referenziale tra una tabella padre e una tabella figlio in un set di dati.

I vincoli specificati in un <xref:System.Data.DataRelation> oggetto vengono implementati creando automaticamente oggetti appropriati o impostando le proprietà. Se si crea un vincolo di chiave esterna utilizzando l' <xref:System.Data.DataRelation> oggetto, le istanze della <xref:System.Data.ForeignKeyConstraint> classe vengono aggiunte alla proprietà dell' <xref:System.Data.DataRelation> oggetto <xref:System.Data.DataRelation.ChildKeyConstraint%2A> .

Un vincolo UNIQUE viene implementato impostando semplicemente la <xref:System.Data.DataColumn.Unique%2A> proprietà di una colonna di dati su `true` o aggiungendo un'istanza della <xref:System.Data.UniqueConstraint> classe alla <xref:System.Data.DataRelation> proprietà dell'oggetto <xref:System.Data.DataRelation.ParentKeyConstraint%2A> . Per informazioni sulla sospensione di vincoli in un set di dati, vedere [disabilitare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Regole di integrità referenziale
Come parte del vincolo FOREIGN KEY, è possibile specificare le regole di integrità referenziale applicate a tre punti:

- Quando viene aggiornato un record padre

- Quando viene eliminato un record padre

- Quando una modifica viene accettata o rifiutata

Le regole che è possibile apportare sono specificate nell' <xref:System.Data.Rule> enumerazione e sono elencate nella tabella seguente.

|Regola vincolo di chiave esterna|Azione|
| - |------------|
|<xref:System.Data.Rule.Cascade>|La modifica (aggiornamento o eliminazione) apportata al record padre viene inoltre apportata in record correlati nella tabella figlio.|
|<xref:System.Data.Rule.SetNull>|I record figlio non vengono eliminati, ma la chiave esterna nei record figlio viene impostata su <xref:System.DBNull> . Con questa impostazione, i record figlio possono essere lasciati come "orfani", ovvero non hanno alcuna relazione con i record padre. **Nota:** L'utilizzo di questa regola può generare dati non validi nella tabella figlio.|
|<xref:System.Data.Rule.SetDefault>|La chiave esterna nei record figlio correlati viene impostata sul valore predefinito, come stabilito dalla proprietà della colonna <xref:System.Data.DataColumn.DefaultValue%2A> .|
|<xref:System.Data.Rule.None>|Non viene apportata alcuna modifica ai record figlio correlati. Con questa impostazione, i record figlio possono contenere riferimenti a record padre non validi.|

Per ulteriori informazioni sugli aggiornamenti nelle tabelle del set di [dati](../data-tools/save-data-back-to-the-database.md), vedere salvare i dati nel database.

### <a name="constraint-only-relations"></a>Relazioni solo vincolo
Quando si crea un <xref:System.Data.DataRelation> oggetto, è possibile specificare che la relazione deve essere utilizzata solo per applicare i vincoli, ovvero non verrà utilizzata anche per accedere ai record correlati. È possibile usare questa opzione per generare un set di dati che è leggermente più efficiente e che contiene un minor numero di metodi rispetto a uno con la funzionalità dei record correlati. Tuttavia, non sarà possibile accedere ai record correlati. Una relazione di solo vincolo, ad esempio, impedisce l'eliminazione di un record padre che contiene ancora record figlio e non è possibile accedere ai record figlio tramite l'elemento padre.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Creazione manuale di una relazione dati nell'Progettazione DataSet
Quando si creano tabelle di dati tramite gli strumenti di progettazione dei dati in Visual Studio, le relazioni vengono create automaticamente se le informazioni possono essere raccolte dall'origine dei dati. Se si aggiungono manualmente tabelle di dati dalla scheda **DataSet** della **casella degli strumenti**, potrebbe essere necessario creare manualmente la relazione. Per informazioni sulla creazione di <xref:System.Data.DataRelation> oggetti a livello di codice, vedere [aggiunta di DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Le relazioni tra le tabelle di dati vengono visualizzate come righe nel **Progettazione DataSet**, con un glifo di chiave e infinito che illustra l'aspetto uno-a-molti della relazione. Per impostazione predefinita, il nome della relazione non viene visualizzato nell'area di progettazione.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Per creare una relazione tra due tabelle di dati

1. Aprire il set di dati in **Progettazione DataSet**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Trascinare un oggetto **relazione** dalla casella degli strumenti del **set** di dati alla tabella dati figlio nella relazione.

     Viene visualizzata la finestra di dialogo **relazione** che popola la casella della **tabella figlio** con la tabella in cui è stato trascinato l'oggetto **relazione** .

3. Selezionare la tabella padre dalla casella **tabella padre** . La tabella padre contiene record sul lato "uno" di una relazione uno-a-molti.

4. Verificare che nella casella **tabella figlio** sia visualizzata la tabella figlio corretta. La tabella figlio contiene record sul lato "molti" di una relazione uno-a-molti.

5. Digitare un nome per la relazione nella casella **nome** o lasciare il nome predefinito in base alle tabelle selezionate. Si tratta del nome dell'oggetto effettivo <xref:System.Data.DataRelation> nel codice.

6. Selezionare le colonne che uniscono le tabelle negli elenchi **colonne chiave** ed **colonne chiave esterna** .

7. Consente di scegliere se creare una relazione, un vincolo o entrambi.

8. Selezionare o deselezionare la casella **relazione nidificata** . Se si seleziona questa opzione <xref:System.Data.DataRelation.Nested%2A> , la proprietà viene impostata su `true` e le righe figlio della relazione verranno annidate all'interno della colonna padre quando tali righe vengono scritte come dati XML o sincronizzate con <xref:System.Xml.XmlDataDocument> . Per ulteriori informazioni, vedere [nidificazione di oggetti DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Impostare le regole da applicare quando si apportano modifiche ai record in queste tabelle. Per altre informazioni, vedere <xref:System.Data.Rule>.

10. Fare clic su **OK** per creare la relazione. Una linea di relazione viene visualizzata nella finestra di progettazione tra le due tabelle.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Per visualizzare un nome di relazione nella Progettazione DataSet

1. Aprire il set di dati in **Progettazione DataSet**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Dal menu **dati** selezionare il comando **Mostra etichette di relazione** per visualizzare il nome della relazione. Deselezionare il comando per nascondere il nome della relazione.

## <a name="see-also"></a>Vedi anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
