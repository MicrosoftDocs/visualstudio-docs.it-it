---
title: Strumenti di set di dati in Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a8c8660fbc489dd8c4926bb09b8b42006da0897a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Strumenti di set di dati in Visual Studio
> [!NOTE]
>  Set di dati e le classi correlate sono tecnologie .NET legacy dal 2000s anticipata che consentono alle applicazioni di utilizzare i dati in memoria, mentre le applicazioni vengono disconnessi dal database. Sono particolarmente utili per le applicazioni che consentono agli utenti di modificare i dati e rendere permanenti le modifiche al database. Sebbene i set di dati si sono rivelate una tecnologia di successo, è consigliabile che le nuove applicazioni .NET usare Entity Framework. Entity Framework fornisce un modo più semplice per utilizzare dati tabulari come modelli a oggetti, e ha un'interfaccia di programmazione più semplice.  
  
 Un oggetto set di dati è un oggetto in memoria che è essenzialmente un mini-database. Contiene gli oggetti DataTable e DataColumn DataRow in cui è possibile archiviare e modificare i dati da uno o più database senza dovere gestire una connessione aperta. Il set di dati mantiene le informazioni sulle modifiche ai dati, pertanto gli aggiornamenti possono essere rilevati e inviati nuovamente al database quando l'applicazione verrà riconnessa.  
  
 Set di dati e le classi correlate sono definite nello spazio dei nomi System. Data nella libreria di classi .NET Framework. È possibile creare e modificare set di dati in modo dinamico nel codice. Per ulteriori informazioni su come eseguire questa operazione, vedere ADO.NET. La documentazione in questa sezione viene illustrato come utilizzare i set di dati tramite le finestre di progettazione di Visual Studio. Una cosa da sapere: set di dati che vengono effettuate tramite le finestre di progettazione utilizzano oggetti TableAdapter per interagire con il database, mentre i set di dati che vengono apportate a livello di programmazione utilizzare oggetti DataAdapter. Per informazioni sulla creazione di set di dati a livello di codice, vedere [DataAdapter e DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
 Se l'applicazione deve solo leggere i dati da un database e non eseguire gli aggiornamenti, aggiunge o Elimina, in genere si ottengono prestazioni migliori utilizzando un oggetto DataReader per recuperare i dati in un oggetto elenco generico o un altro oggetto della raccolta. Se si visualizzano i dati, è possibile associare l'interfaccia utente alla raccolta.  
  
## <a name="dataset-workflow"></a>Flusso di lavoro di set di dati  
 Visual Studio fornisce numerosi strumenti per semplificare l'utilizzo di set di dati. Il flusso di lavoro end-to-end base è:  
  
-   Utilizzare il **origine dati** finestra consente di creare un nuovo set di dati da uno o più origini dati. Utilizzare il **Progettazione Dataset** per configurare il set di dati e impostare le relative proprietà. Ad esempio, è necessario specificare quali tabelle dell'origine dati da includere e le colonne di ogni tabella. Scegliere con attenzione conservare la quantità di memoria che richiede il set di dati. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).  
  
-   Specificare le relazioni tra le tabelle in modo che le chiavi esterne vengono gestite correttamente. Per ulteriori informazioni, vedere [riempire i set di dati utilizzando gli oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Utilizzare il **configurazione guidata TableAdapter** per specificare la query o stored procedure in grado di popolare il set di dati e le operazioni di database (update, delete e così via) da implementare. Per altre informazioni, vedere gli argomenti seguenti:  
  
    -   [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Modificare i dati nei set di dati](../data-tools/edit-data-in-datasets.md)  
  
    -   [Convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md)  
  
    -   [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)  
  
-   Eseguire una query e cercare i dati nel set di dati. Per ulteriori informazioni, vedere [set di dati di Query](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]Abilita [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) su dati in un <xref:System.Data.DataSet> oggetto. Per altre informazioni, vedere [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
-   Utilizzare il **origini dati** finestra consente di associare i controlli dell'interfaccia utente per il set di dati o le singole colonne e per specificare quali colonne sono modificabili dall'utente. Per ulteriori informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="datasets-and-n-tier-architecture"></a>Architettura di set di dati e a più livelli  
 Per informazioni sui set di dati nelle applicazioni a più livelli, vedere [utilizzano set di dati nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md).  
  
## <a name="datasets-and-xml"></a>Set di dati e XML  
 Per informazioni sulla conversione dei set di dati in e da XML, vedere [legge i dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md) e [salvare un dataset come XML](../data-tools/save-a-dataset-as-xml.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)