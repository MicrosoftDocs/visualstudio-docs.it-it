---
title: Salvare i dati con DBDirect di TableAdapter metodi | Documenti Microsoft
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 628a3cfc75f786ceb989145ada6e2f2579f349cd
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Salvare i dati con DBDirect di TableAdapter metodi
Questa procedura dettagliata vengono fornite istruzioni dettagliate per l'esecuzione di istruzioni SQL direttamente in un database utilizzando i metodi DBDirect di un oggetto TableAdapter. I metodi DBDirect di un oggetto TableAdapter forniscono un elevato livello di controllo degli aggiornamenti del database. È possibile usarli per eseguire istruzioni SQL specifiche e stored procedure chiamando i singoli `Insert`, `Update`, e `Delete` metodi in base alle esigenze dell'applicazione (a differenza di overload `Update` metodo che esegue l'aggiornamento Istruzioni INSERT e DELETE in un'unica chiamata).  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare un nuovo **applicazione Windows Form**.  
  
-   Creare e configurare un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Selezionare il controllo da creare sul form quando si trascinano elementi dal **origini dati** finestra. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creare un form associato a dati trascinando elementi dal **origini dati** finestra al form.  
  
-   Aggiungere metodi per accedere al database direttamente ed eseguire inserimenti, aggiornamenti ed eliminazioni...  
  
## <a name="prerequisites"></a>Prerequisiti  
Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.  
  
1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.  
  
2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:  

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .  

       Verrà visualizzata una finestra dell'editor di query.  

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.  

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.  

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.  
  
## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Form  
 Il primo passaggio consiste nel creare un **applicazione Windows Form**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .  
  
2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.  

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.  

4. Denominare il progetto **TableAdapterDbDirectMethodsWalkthrough**, quindi scegliere **OK**. 
  
     Il **TableAdapterDbDirectMethodsWalkthrough** progetto viene creato e aggiunto a **Esplora**.  
  
## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database  
 Questo passaggio viene utilizzata la **configurazione guidata origine dati** per creare un'origine dati basata sul `Region` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sull'impostazione di database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Nel **dati** dal menu **Mostra origini dati**.  
  
2.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati**.  
  
3.  Nel **scegliere un tipo di origine dati** selezionare **Database**, quindi selezionare **Avanti**.  
  
4.  Nel **Seleziona connessione dati** schermata, effettuare una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         oppure  
  
    -   Selezionare **nuova connessione** per avviare il **Aggiungi/Modifica connessione** la finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati riservati, quindi selezionare **Avanti**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti**.  
  
7.  Nel **Seleziona oggetti di Database** schermata, quindi espandere il **tabelle** nodo.  
  
8.  Selezionare il `Region` tabella e quindi selezionare **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e `Region` tabella viene visualizzata nella **origini dati** finestra.  
  
## <a name="add-controls-to-the-form-to-display-the-data"></a>Aggiungere controlli al form per visualizzare i dati  
 Creare i controlli con associazione a dati trascinando elementi dal **origini dati** finestra nel form.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare i dati associati a controlli in Windows form  
  
-   Trascinare principale **area** nodo dal **origini dati** finestra al form.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Per aggiungere pulsanti da usare per la chiamata ai singoli metodi DbDirect di TableAdapter  
  
1.  Trascinare i tre <xref:System.Windows.Forms.Button> dei controlli di **della casella degli strumenti** nella **Form1** (sotto il **RegionDataGridView**).  
  
2.  Impostare le seguenti **nome** e **testo** proprietà su ogni pulsante.  
  
    |nome|Testo|  
    |----------|----------|  
    |`InsertButton`|**Inserisci**|  
    |`UpdateButton`|**Aggiornamento**|  
    |`DeleteButton`|**Eliminazione**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Per aggiungere il codice per l'inserimento dei nuovi record nel database  
  
1.  Selezionare **InsertButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.  
  
2.  Sostituire il gestore eventi `InsertButton_Click` con il codice seguente:  
  
     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Per aggiungere il codice per l'aggiornamento dei record nel database  
  
1.  Fare doppio clic su di **UpdateButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.  
  
2.  Sostituire il gestore eventi `UpdateButton_Click` con il codice seguente:  
  
     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Per aggiungere codice per eliminare i record dal database  
  
1.  Selezionare **DeleteButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.  
  
2.  Sostituire il gestore eventi `DeleteButton_Click` con il codice seguente:  
  
     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]  
  
## <a name="run-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Selezionare **F5** per eseguire l'applicazione.  
  
-   Selezionare il **inserire** pulsante e verificare che il nuovo record venga visualizzato nella griglia.  
  
-   Selezionare il **aggiornamento** pulsante e verificare che il record viene aggiornato nella griglia.  
  
-   Selezionare il **eliminare** pulsante e verificare che il record viene rimosso dalla griglia.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, esistono diverse operazioni che si desidera eseguire dopo la creazione di un form associato a dati. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di funzionalità di ricerca al form.  
  
-   Aggiunta di altre tabelle al set di dati selezionando **configura il DataSet con Creazione guidata** dall'interno di **origini dati** finestra. È possibile aggiungere controlli che consentono di visualizzare dati correlati mediante il trascinamento dei nodi correlati nel form. Per ulteriori informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)