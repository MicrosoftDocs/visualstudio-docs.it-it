---
title: Creare e configurare i set di dati in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d7aac502f32941d825fda77c43ae07e82c4e9db3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Creare e configurare i set di dati in Visual Studio

Oggetto *set di dati* è un set di oggetti che archiviano i dati da un database in memoria e supportano il rilevamento delle modifiche per abilitare creare, leggere, aggiornare e l'eliminazione (CRUD) sui dati senza la necessità di essere sempre connessi al database. Set di dati sono stati progettati per semplice *form su dati* applicazioni aziendali. Per le nuove applicazioni, prendere in considerazione l'utilizzo di Entity Framework per archiviare e modellare i dati in memoria. Per utilizzare i set di dati, è necessario una conoscenza di base dei concetti di database.

Si crea un oggetto tipizzato <xref:System.Data.DataSet> classe in Visual Studio in fase di progettazione utilizzando il **configurazione guidata origine dati**. Per informazioni sulla creazione di set di dati a livello di codice, vedere [la creazione di un set di dati (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Creare un nuovo set di dati utilizzando la configurazione guidata origine dati

1.  Nel **progetto** menu, fare clic su **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati**.

2.  Scegliere il tipo dell'origine dati che connetterà.

     ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png "configurazione guidata origine dati")

3.  Per i database, scegliere i database che sarà l'origine dati per il set di dati.

     ![Origine dati scegliere una connessione](../data-tools/media/data-source-choose-a-connection.png "origine dati scegliere una connessione")

4.  Scegliere le tabelle (o singole colonne), stored procedure, funzioni e viste dal database che si desidera essere rappresentato nel set di dati.

     ![Scegliere gli oggetti di database](../data-tools/media/raddata-chose-objects.png "raddata scelto oggetti")

5.  Scegliere **Fine**.

6.  Il set di dati viene visualizzato come un nodo in **Esplora**:

     ![Set di dati in Esplora soluzioni](../data-tools/media/dataset-in-solution-explorer.png "set di dati in Esplora soluzioni")

     Fare clic su tale nodo, e il set di dati verrà visualizzata la **Progettazione DataSet**. Si noti che ogni tabella nel set di dati è associato un oggetto TableAdapter, che è rappresentato nella parte inferiore. Adattatore di tabella viene utilizzato per popolare il set di dati e, facoltativamente, per inviare comandi al database.

     ![Progettazione DataSet](../data-tools/media/dataset-designer.png "Progettazione DataSet")

7.  Le linee di relazione che si connettono le tabelle rappresentano le relazioni tra tabelle, come definito nel database. Per impostazione predefinita, i vincoli di chiave esterna in un database vengono rappresentati come una relazione solo con l'aggiornamento ed eliminare le regole impostate su none. In genere, che è quello desiderato. Tuttavia, è possibile fare clic su righe da visualizzare il **relazione** finestra di dialogo, in cui è possibile modificare il comportamento degli aggiornamenti gerarchici. Per ulteriori informazioni, vedere [relazioni nei DataSet](../data-tools/relationships-in-datasets.md) e [aggiornamento gerarchico](../data-tools/hierarchical-update.md).

     ![Finestra di dialogo relazione DataSet](../data-tools/media/raddata-relation-dialog.png "finestra di dialogo relazione raddata")

8.  Fare clic su una tabella, l'adattatore di tabella o il nome di colonna in una tabella per visualizzare le proprietà nel **proprietà** finestra. È possibile modificare alcuni dei valori di. Ricordare che si modifica il set di dati, non il database di origine.

     ![Proprietà set di dati colonna](../data-tools/media/dataset-column-properties.png "proprietà set di dati colonna")

9. È possibile aggiungere nuove tabelle o gli adattatori di tabella per il set di dati o aggiungere nuove query per gli adattatori di tabella esistente o specificare nuove relazioni tra tabelle trascinando gli elementi dal **della casella degli strumenti** scheda. Questa scheda viene visualizzato quando il **Progettazione DataSet** lo stato attivo.

     ![Set di dati della casella degli strumenti](../data-tools/media/raddata-dataset-toolbox.png "raddata set di dati della casella degli strumenti")

10. Successivamente, si potrebbe essere necessario specificare come popolare il set di dati con i dati. A tale scopo, utilizzare il **configurazione guidata TableAdapter**. Per ulteriori informazioni, vedere [riempire i set di dati utilizzando gli oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Aggiungere una tabella di database o un altro oggetto a un set di dati esistente

Questa procedura viene illustrato come aggiungere una tabella dallo stesso database utilizzato per creare innanzitutto il set di dati.

1.  Fare clic sul nodo di set di dati in **Esplora** per rendere la finestra di progettazione del set di dati attivo.

2.  Fare clic su di **origini dati** scheda nel margine sinistro di Visual Studio o immettere `Data Sources` in **veloce**.

3.  Il nodo di set di dati e scegliere **Configura origine dati con Creazione guidata**.

     ![Menu di scelta rapida origine dati](../data-tools/media/data-source-context-menu.png "menu di scelta rapida origine dati")

4.  Utilizzare la procedura guidata per specificare quali tabelle aggiuntive, o le stored procedure o un altro oggetto di database, da aggiungere al set di dati.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Aggiungere una tabella dati autonomo a un set di dati

1.  Aprire il dataset nel **Progettazione Dataset**.

2.  Trascinare un <xref:System.Data.DataTable> classe il **set di dati** scheda della finestra il **della casella degli strumenti** nel **Progettazione Dataset**.

3.  Aggiungere colonne per definire la tabella dati. Fare doppio clic sulla tabella e scegliere **Aggiungi > colonna**. Utilizzare il **proprietà** finestra per impostare il tipo di dati della colonna e una chiave, se necessario.

4.  Le tabelle autonome necessario implementare `Fill` logica nelle tabelle autonome in modo che è possibile inserire i dati. Per informazioni su come inserire le tabelle di dati autonomo, vedere [popolamento di un set di dati da un oggetto DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)