---
title: Aggiungere nuove origini dati
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: efcc167ba42469aa8e32198161612db7521d22ba
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="add-new-data-sources"></a>Aggiungere nuove origini dati
Nel contesto di strumenti di dati .NET in Visual Studio, il termine *origine dati* fa riferimento a oggetti .NET che si connettono a un archivio dati e di espongono i dati a un'applicazione .NET. Le finestre di progettazione di Visual Studio possono usare l'output dell'origine dati per generare il codice boilerplate che associa i dati a un form quando si trascinano gli oggetti di database di **origini dati** finestra. Questo tipo di origine dati può essere:

-   Una classe in un modello di Entity Framework che è associata a un tipo di database.

-   Un set di dati è associata a un tipo di database.

-   Una classe che rappresenta un servizio di rete, ad esempio un servizio dati di Windows Communication Foundation (WCF) o un servizio REST.

-   Una classe che rappresenta un servizio di SharePoint.

-   Una classe o una raccolta nella soluzione.

> [!NOTE]
>  Se non si utilizzano funzionalità di associazione dati, set di dati, Entity Framework, LINQ to SQL, WCF o SharePoint, il concetto di "data source" non è applicabile. È sufficiente connettersi direttamente al database utilizzando gli oggetti di SQLCommand e comunicare direttamente con il database.

 Per creare e modificare origini dati utilizzando il **configurazione guidata origine dati** in un'applicazione Windows Form o Windows Presentation Foundation. Prima di creare classi di entità per Entity Framework, e quindi avviare la procedura guidata selezionando **progetto** > **Aggiungi nuova origine dati** (descritto in dettaglio più avanti in questo articolo).

 ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png "configurazione guidata origine dati")

 Dopo aver creato un'origine dati, viene visualizzato nel **origini dati** finestra degli strumenti (Maiusc + Alt + D o **vista** > **altre finestre**  >  **Origine dati**). È possibile trascinare un'origine dati dal **origini dati** finestra un controllo o l'area di progettazione form. In questo modo il codice di boilerplate da generare, ovvero codice che visualizza i dati che hanno origine nell'archivio dati per l'utente. Nella figura seguente viene illustrato un set di dati che è stato eliminato in un Windows form. Se si seleziona F5 sull'applicazione, i dati dal database sottostante appariranno nei controlli del form.

 ![Operazione di trascinamento di origine dati](../data-tools/media/raddata-data-source-drag-operation.png "operazione di trascinamento raddata origine dati")

## <a name="data-source-for-a-database-or-a-database-file"></a>Origine dati per un database o un file di database

### <a name="dataset"></a>Set di dati
 Per creare un set di dati come origine dati, eseguire il **configurazione guidata origine dati** (**progetto** > **Aggiungi nuova origine dati**) e scegliere il  **Database** tipo di origine dati. Seguire le istruzioni per specificare una connessione di database nuovo o esistente o un file di database.

### <a name="entity-classes"></a>Classi di entità
 Per creare un modello di Entity Framework come origine dati, eseguire innanzitutto il **procedura guidata Entity Data Model** per creare le classi di entità (**progetto** > **Aggiungi nuovo elemento**  >  **ADO.NET Entity Data Model**).

 ![Nuovo elemento di progetto di modello di Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata elemento del progetto modello nuovo Entity Framework")

 Scegliere il metodo mediante il quale si desidera generare il modello.

 ![Procedura guidata Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "raddata procedura guidata Entity Data Model")

 Aggiungere il modello come origine dati. Le classi generate vengono visualizzate nel **configurazione guidata origine dati** quando si sceglie il **oggetti** categoria.

 ![Configurazione guidata origine dati con le classi di entità](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata configurazione guidata origine dati con le classi di entità")

## <a name="data-source-for-a-service"></a>Origine dati per un servizio
 Per creare un'origine dati da un servizio, eseguire il **configurazione guidata origine dati** e scegliere il **servizio** tipo di origine dati. Si tratta in realtà solo un collegamento di **Aggiungi riferimento al servizio** nella finestra di dialogo è inoltre possibile accedere facendo clic con il progetto in **Esplora** e selezionando **Aggiungi riferimento al servizio** .

 Quando si crea un'origine dati da un servizio, Visual Studio aggiunge un riferimento al servizio al progetto. Visual Studio crea anche gli oggetti proxy che corrispondono agli oggetti restituite dal servizio. Ad esempio, un servizio che restituisce un set di dati è rappresentato nel progetto come un set di dati; un servizio che restituisce che un tipo specifico è rappresentato nel progetto come tipo restituito.

 Uno dei seguenti tipi di servizi, è possibile creare un'origine dati:

-   WCF Data Services. Per ulteriori informazioni, vedere [Panoramica](/dotnet/framework/data/wcf/wcf-data-services-overview).

-   Servizi WCF. Per ulteriori informazioni, vedere [servizi Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).

-   Servizi Web.

    > [!NOTE]
    >  Gli elementi visualizzati nel **origini dati** finestra dipendono i dati che restituisce il servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti affinché il **configurazione guidata origine dati** per creare oggetti associabili. Ad esempio, se il servizio restituisce un dataset non tipizzato, verrà visualizzato alcun elemento nella **origini dati** finestra una volta completata la procedura guidata. In questo modo DataSet non tipizzati non forniscono uno schema, e pertanto la procedura guidata non ha informazioni sufficienti per creare l'origine dati.

## <a name="data-source-for-an-object"></a>Origine dati per un oggetto
 È possibile creare un'origine dati da qualsiasi oggetto che espone uno o più proprietà pubbliche eseguendo il **configurazione guidata origine dati** e quindi selezionando il **oggetto** tipo di origine dati. Cui vengono visualizzate tutte le proprietà pubbliche di un oggetto di **origini dati** finestra.   Se si utilizza Entity Framework e hanno generato un modello, si tratta di dove è trovare le classi di entità che saranno le origini dati per l'applicazione.

 Nel **selezionare gli oggetti dati** pagina, espandere i nodi nella visualizzazione albero per individuare gli oggetti che si desidera associare. La visualizzazione albero contiene nodi per il progetto e per l'assembly e altri progetti a cui fa riferimento il progetto.

 Se si desidera associare a un oggetto in un assembly o un progetto che non viene visualizzato nella visualizzazione albero, fare clic su **Aggiungi riferimento** e utilizzare il **dialogo Aggiungi riferimento** per aggiungere un riferimento all'assembly o al progetto. Dopo aver aggiunto il riferimento, l'assembly o il progetto viene aggiunto alla visualizzazione albero.

> [!NOTE]
>  Potrebbe essere necessario compilare il progetto che contiene gli oggetti prima che gli oggetti vengono visualizzati nella visualizzazione albero.

> [!NOTE]
>  Per supportare l'associazione di dati di trascinamento e rilascio, gli oggetti che implementano il <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaccia deve avere un costruttore predefinito. In caso contrario, Visual Studio non è possibile creare un'istanza di oggetto origine dati e verrà visualizzato un errore quando si trascina l'elemento nell'area di progettazione.

## <a name="data-source-for-a-sharepoint-list"></a>Origine dati per un elenco SharePoint
 È possibile creare un'origine dati da un elenco SharePoint eseguendo il **configurazione guidata origine dati** e selezionando il **SharePoint** tipo di origine dati. Espone i dati mediante SharePoint [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], pertanto la creazione di un'origine dati SharePoint è analoga alla creazione di un'origine dati da un servizio. Selezione di **SharePoint** elemento il **configurazione guidata origine dati** apre il **Aggiungi riferimento al servizio** nella finestra di dialogo in cui connettono al servizio dati di SharePoint facendo riferimento al server di SharePoint.  Questa operazione richiede il SDK di SharePoint.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)