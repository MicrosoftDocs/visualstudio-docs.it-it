---
title: 'Procedura dettagliata: Creazione di un set di dati con Progettazione Dataset | Documenti Microsoft'
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 35f98e7442c6600baa1afcc38642abf8e7aeb3ba
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Procedura dettagliata: creazione di un dataset con Progettazione DataSet

In questa procedura dettagliata verrà creato un set di dati usando il **Progettazione Dataset**. Verrà illustrato il processo di creazione di un nuovo progetto e aggiungendo un nuovo **DataSet** elemento a esso. Si apprenderà come creare tabelle in base alle tabelle in un database senza utilizzare una procedura guidata.  

Le attività illustrate nella procedura dettagliata sono le seguenti:  

-   Creazione di un nuovo **Windows Forms Application** progetto.  

-   Aggiunta di un oggetto vuoto **DataSet** elemento al progetto.  

-   Creazione e configurazione di un'origine dati nell'applicazione creando un set di dati con il **Progettazione Dataset**.  
 
-   Creazione di una connessione al database Northwind in **Esplora Server**.  

-   Creazione di tabelle con gli oggetti TableAdapter nel set di dati in base alle tabelle nel database.  

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.  
  
1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.  
  
2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:  

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .  

       Verrà visualizzata una finestra dell'editor di query.  

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.  

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.  

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.  
  
## <a name="creating-a-new-windows-forms-application-project"></a>Creazione di un nuovo progetto di applicazione Windows Form  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Per creare un nuovo progetto applicazione Windows Form  
  
1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .  
  
2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.  

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.  

4. Denominare il progetto **nome DatasetDesignerWalkthrough**, quindi scegliere **OK**.  
  
     Visual Studio aggiunge il progetto a **Esplora** e visualizzato un nuovo form nella finestra di progettazione.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Aggiunta di un nuovo set di dati all'applicazione  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Per aggiungere un nuovo elemento di set di dati al progetto  
  
1.  Nel **progetto** dal menu **Aggiungi nuovo elemento...** .  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nel riquadro a sinistra, selezionare **dati**, quindi selezionare **DataSet** nel riquadro centrale.  
  
3.  Nome del set di dati **NorthwindDataset**, quindi scegliere **Aggiungi**.  
  
     Visual Studio aggiunge un file denominato **NorthwindDataset.xsd** al progetto e aprirlo nel **Progettazione Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Creazione di una connessione dati in Esplora Server  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Per creare una connessione al database Northwind  
  
1.  Nel **vista** menu, fare clic su **Esplora Server**.  
  
2.  In **Esplora Server**, fare clic su di **Connetti al Database** pulsante.  
  
3.  Creare una connessione al database di esempio Northwind.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Creazione di tabelle nel set di dati  
In questa sezione viene illustrato come aggiungere tabelle al set di dati.  
  
#### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers  
  
1.  Espandere la connessione dati è stato creato in **Esplora Server**, quindi espandere il **tabelle** nodo.  
  
2.  Trascinare il **clienti** tabella **Esplora Server** sul **Progettazione Dataset**.  
  
     Oggetto **clienti** tabella dati e **CustomersTableAdapter** vengono aggiunti al set di dati.  
  
#### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders  
  
-   Trascinare il **ordini** tabella **Esplora Server** sul **Progettazione Dataset**.  
  
     Un **ordini** tabella dati, **OrdersTableAdapter**e relazione dati tra il **clienti** e **ordini** tabelle vengono aggiunte al set di dati.  
  
#### <a name="to-create-the-orderdetails-table"></a>Per creare la tabella OrderDetails  
  
-   Trascinare il **Order Details** tabella **Esplora Server** sul **Progettazione Dataset**.  
  
     Un **Order Details** tabella dati, **OrderDetailsTableAdapter**e una relazione dati tra il **ordini** e **OrderDetails** tabelle vengono aggiunti al set di dati.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
### <a name="to-add-functionality-to-your-application"></a>Per aggiungere funzionalità all'applicazione  
  
-   Salvare il set di dati.  
  
-   Selezionare gli elementi di **origini dati** finestra e trascinarli in un form. Per ulteriori informazioni, vedere [controlli binding di Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Aggiungere più query per gli oggetti TableAdapter. 
  
-   Aggiungere la logica di convalida per il <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> gli eventi delle tabelle di dati nel set di dati. Per ulteriori informazioni, vedere [convalidare i dati in set di dati](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vedere anche
[Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Convalida dei dati](../data-tools/validate-data-in-datasets.md)   
[Salvataggio di dati](../data-tools/saving-data.md)