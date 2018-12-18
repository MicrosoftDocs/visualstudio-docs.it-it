---
title: Consente di creare relazioni tra i set di dati DataRelation | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 95bfef50e7ce5016b68df1442e625a88beb22181
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="create-relationships-between-datasets"></a>Creare relazioni tra i set di dati
Tabelle di set di dati che contengono dati correlati utilizzano <xref:System.Data.DataRelation> oggetti per rappresentare una relazione padre/figlio tra le tabelle e per restituire i record correlati tra loro. Aggiunta di tabelle correlate ai set di dati utilizzando il **configurazione guidata origine dati**, o **Progettazione Dataset**, crea e configura il <xref:System.Data.DataRelation> oggetto.  
  
Il <xref:System.Data.DataRelation> oggetto svolge due funzioni:  
  
-   È possibile rendere disponibili i record correlati a un record che si sta utilizzando. Fornisce i record figlio in un record padre (<xref:System.Data.DataRow.GetChildRows%2A>) e un record padre, se si lavora con un record figlio (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
-   È possibile applicare vincoli di integrità referenziale, ad esempio l'eliminazione di record figlio correlati quando si elimina un record padre.  
  
È importante comprendere la differenza tra un join e la funzione di un <xref:System.Data.DataRelation> oggetto. In un join, i record vengono ricavati dalle tabelle padre e figlio e inseriti in un unico set di record. Quando si utilizza un <xref:System.Data.DataRelation> dell'oggetto, non viene creato alcun nuovo recordset. Al contrario, DataRelation tiene traccia della relazione tra tabelle e sincronizzazione record padre e figlio.  
  
## <a name="datarelation-objects-and-constraints"></a>I vincoli e gli oggetti DataRelation  
Oggetto <xref:System.Data.DataRelation> oggetto viene usato anche per creare e imporre i vincoli seguenti:  
  
-   Un vincolo univoco, che garantisce che una colonna nella tabella non contiene duplicati.  
  
-   Un vincolo di chiave esterna, che può essere usato per mantenere l'integrità referenziale tra una tabella padre e figlio in un set di dati.  
  
I vincoli specificati in un <xref:System.Data.DataRelation> oggetto vengono implementate automaticamente la creazione di oggetti appropriati o impostando le proprietà. Se si crea un vincolo foreign key utilizzando il <xref:System.Data.DataRelation> oggetto, le istanze del <xref:System.Data.ForeignKeyConstraint> classe vengono aggiunti per il <xref:System.Data.DataRelation> dell'oggetto <xref:System.Data.DataRelation.ChildKeyConstraint%2A> proprietà.  
  
Viene implementato un vincolo unique impostando semplicemente il <xref:System.Data.DataColumn.Unique%2A> proprietà di una colonna di dati per `true` o mediante l'aggiunta di un'istanza del <xref:System.Data.UniqueConstraint> classe per il <xref:System.Data.DataRelation> dell'oggetto <xref:System.Data.DataRelation.ParentKeyConstraint%2A> proprietà. Per informazioni sulla sospensione dei vincoli in un set di dati, vedere [disattivare i vincoli durante la compilazione di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Regole di integrità referenziale  
Come parte del vincolo di chiave esterna, è possibile specificare regole di integrità referenziale che vengono applicate in tre punti:  
  
-   Quando viene aggiornato un record padre  
  
-   Quando viene eliminato un record padre  
  
-   Quando una modifica è accettata o rifiutata  
  
Vengono specificate le regole che è possibile apportare nel <xref:System.Data.Rule> enumerazione ed elencate nella tabella seguente.  
  
|Regola del vincolo di chiave esterna|Operazione|  
|----------------------------------|------------|  
|<xref:System.Data.Rule.Cascade>|La modifica (aggiornamento o eliminazione) apportata al record padre è effettuata anche nel record correlati nella tabella figlio.|  
|<xref:System.Data.Rule.SetNull>|Record figlio non vengono eliminati, ma la relativa chiave esterna viene impostata su <xref:System.DBNull>. Con questa impostazione, i record figlio possono essere lasciati come "orfani", che è non disponibile alcuna relazione con i record padre. **Nota:** usando questa regola può generare dati non validi nella tabella figlio.|  
|<xref:System.Data.Rule.SetDefault>|La chiave esterna nei record figlio correlati viene impostata sul valore predefinito (come stabilito in base alla colonna <xref:System.Data.DataColumn.DefaultValue%2A> proprietà).|  
|<xref:System.Data.Rule.None>|Viene apportata alcuna modifica ai record figlio correlati. Con questa impostazione, i record figlio possono contenere riferimenti a record padre non valido.|  
  
Per ulteriori informazioni sugli aggiornamenti nelle tabelle di set di dati, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Relazioni di solo vincolo  
Quando si crea un <xref:System.Data.DataRelation> dell'oggetto, è possibile scegliere di specificare che la relazione venga utilizzata solo per imporre vincoli, ovvero, ovvero non verrà anche essere utilizzato per accedere ai record correlati. È possibile utilizzare questa opzione per generare un set di dati che è leggermente più efficiente e che contiene metodi di un numero inferiore rispetto a uno con la funzionalità di record correlati. Tuttavia, non sarà in grado di accedere ai record correlati. Ad esempio, una solo vincolo di relazione non è possibile eliminare un record padre che dispone ancora di record figlio e i record figlio non è possibile accedere tramite l'elemento padre.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Creazione manuale di una relazione dati in Progettazione Dataset  
Quando si creano tabelle di dati utilizzando gli strumenti di progettazione di dati in Visual Studio, vengono create automaticamente relazioni se le informazioni possono essere raccolte dall'origine dei dati. Se si aggiungono manualmente le tabelle di dati dal **set di dati** scheda della finestra di **della casella degli strumenti**, potrebbe essere necessario creare manualmente la relazione. Per informazioni sulla creazione di <xref:System.Data.DataRelation> degli oggetti a livello di codice, vedere [aggiunta di oggetti DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).  
  
Le relazioni tra tabelle di dati vengono visualizzati come righe di **Progettazione Dataset**, con una chiave e infinito un'icona che rappresenta l'aspetto uno-a-molti della relazione. Per impostazione predefinita, il nome della relazione non è visualizzato nell'area di progettazione.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Per creare una relazione tra due tabelle dati  
  
1.  Aprire il dataset nel **Progettazione Dataset**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Trascinare un **relazione** dall'oggetto di **set di dati** della casella degli strumenti nella tabella dati figlio nella relazione.  
  
     Il **relazione** verrà visualizzata la finestra di dialogo, la compilazione di **tabella figlio** casella con la tabella trascinata il **relazione** dell'oggetto nella.  
  
3.  Selezionare la tabella padre di **tabella padre** casella. La tabella padre contiene i record sul lato "uno" di una relazione uno-a-molti.  
  
4.  Verificare che la tabella figlio corretto sia visualizzata nel **tabella figlio** casella. La tabella figlio contiene i record sul lato "molti" di una relazione uno-a-molti.  
  
5.  Digitare un nome per la relazione nel **nome** casella o lasciare il nome predefinito in base alle tabelle selezionate. Questo è il nome dell'effettivo <xref:System.Data.DataRelation> oggetto nel codice.  
  
6.  Selezionare le colonne che uniscono in join le tabelle nel **colonne chiave** e **colonne di chiave esterna** Elenca.  
  
7.  Scegliere se creare una relazione, il vincolo o entrambi.   
  
8.  Selezionare o deselezionare il **relazione annidata** casella. Selezionando questa opzione imposta la <xref:System.Data.DataRelation.Nested%2A> proprietà `true`, e il figlio le righe della relazione vengono annidate all'interno della colonna padre quando le righe vengono scritte come dati XML o sincronizzate con <xref:System.Xml.XmlDataDocument>. Per ulteriori informazioni, vedere [annidamento di oggetti DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).  
  
9. Impostare le regole da applicare quando si apportano modifiche ai record in queste tabelle. Per altre informazioni, vedere <xref:System.Data.Rule>.  
  
10. Fare clic su **OK** per creare la relazione. Verrà visualizzata una linea di relazione tra le due tabelle della finestra di progettazione.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Per visualizzare un nome di relazione in Progettazione Dataset  
  
1.  Aprire il dataset nel **Progettazione Dataset**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Dal **dati** menu, seleziona il **Mostra etichette di relazione** comando per visualizzare il nome della relazione. Deselezionare il comando per nascondere il nome della relazione.

## <a name="see-also"></a>Vedere anche
[Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)