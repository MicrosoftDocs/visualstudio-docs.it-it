---
title: 'Procedura dettagliata: Data Binding complesso in un progetto a livello di documento | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a46a0f30fe3ab0cfc44a4cdb9121c4f39f3c417f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Procedura dettagliata: associazione di dati complessa in un progetto a livello di documento
  Questa procedura dettagliata illustra le nozioni fondamentali sull'associazione dati complessa in un progetto a livello di documento. È possibile associare più celle in un foglio di lavoro di Microsoft Office Excel a campi nel database Northwind di SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di un'origine dati per il progetto di cartella di lavoro.  
  
-   Aggiunta di controlli con associazione a dati a un foglio di lavoro.  
  
-   Salvataggio delle modifiche di dati nel database.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server con il database di esempio Northwind di SQL Server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto  
 Il primo passaggio consiste nel creare un progetto cartella di lavoro di Excel.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto di cartella di lavoro di Excel con il nome **risorse del Data Binding complesso**. Nella procedura guidata, selezionare **creare un nuovo documento**.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **risorse del Data Binding complesso** progetto **Esplora**.  
  
## <a name="creating-the-data-source"></a>Creazione dell'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Se la finestra **Origini dati** non è visibile, visualizzarla scegliendo **Visualizza**, **Altre finestre**e **Origini dati**dalla barra dei menu.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e quindi fare clic su **Avanti**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind, o aggiungere una nuova connessione utilizzando il **nuova connessione** pulsante.  
  
5.  Dopo una connessione è stata selezionata o creata, fare clic su **Avanti**.  
  
6.  Deselezionare l'opzione per salvare la connessione se è selezionata, quindi scegliere **Avanti**.  
  
7.  Espandere il **tabelle** nodo il **oggetti di Database** finestra.  
  
8.  Selezionare la casella di controllo accanto al **dipendenti** tabella.  
  
9. Scegliere **Fine**.  
  
 La procedura guidata aggiunge il **dipendenti** tabella il **origini dati** finestra. Aggiunge un dataset tipizzato al progetto che è visibile in **Esplora**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Aggiunta di controlli al foglio di lavoro  
 Verrà visualizzato un foglio di lavoro di **dipendenti** tabella quando viene aperta la cartella di lavoro. Gli utenti saranno in grado di apportare modifiche ai dati e quindi salvare le modifiche al database facendo clic su un pulsante.  
  
 Per associare automaticamente il foglio di lavoro per la tabella, è possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo al foglio di lavoro dal **origini dati** finestra. Per consentire all'utente di salvare le modifiche, aggiungere un <xref:System.Windows.Forms.Button> controllo il **della casella degli strumenti**.  
  
#### <a name="to-add-a-list-object"></a>Per aggiungere un oggetto elenco  
  
1.  Verificare che il **My Binding.xlsx dati complessi** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.  
  
2.  Aprire il **origini dati** window e selezionare il **dipendenti** nodo.  
  
3.  Fare clic sulla freccia a discesa visualizzata.  
  
4.  Selezionare **ListObject** nell'elenco a discesa.  
  
5.  Trascinare il **dipendenti** alla cella **A6**.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato `EmployeesListObject` viene creato nella cella **A6**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `EmployeesBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> istanza vengono aggiunti al progetto. Il controllo è associato al <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato il <xref:System.Data.DataSet> istanza.  
  
#### <a name="to-add-a-button"></a>Per aggiungere un pulsante  
  
1.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **A4** del foglio di lavoro.  
  
 Il passaggio successivo consiste nell'aggiungere testo al pulsante quando viene aperto il foglio di lavoro.  
  
## <a name="initializing-the-control"></a>Inizializzazione del controllo  
 Aggiungere testo al pulsante il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> gestore dell'evento.  
  
#### <a name="to-initialize-the-control"></a>Per inizializzare il controllo  
  
1.  In **Esplora**, fare doppio clic su **Sheet1. vb** o **Sheet1. cs**, quindi fare clic su **Visualizza codice** nel menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il `Sheet1_Startup` per impostare il testo per b`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  Solo per c#, aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento per il `Sheet1_Startup` metodo.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 A questo punto aggiungere il codice per gestire il <xref:System.Windows.Forms.Control.Click> evento del pulsante.  
  
## <a name="saving-changes-to-the-database"></a>Salvare le modifiche al Database  
 Sono state apportate modifiche per i dati disponibili solo nel set di dati locale finché non vengono salvati in modo esplicito nel database.  
  
#### <a name="to-save-changes-to-the-database"></a>Salvare le modifiche al database  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento di b`utton`e aggiungere il codice seguente per eseguire il commit di tutte le modifiche apportate nel set di dati nel database.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare la cartella di lavoro per verificare che i dati vengono visualizzati come previsto e che sia possibile modificare i dati nell'oggetto elenco.  
  
#### <a name="to-test-the-data-binding"></a>Per verificare l'associazione dati  
  
-   Premere F5.  
  
     Verificare che quando si apre la cartella di lavoro, il controllo ListObject con dati di **dipendenti** tabella.  
  
#### <a name="to-modify-data"></a>Per modificare i dati  
  
1.  Fare clic sulla cella **B7**, che deve contenere il nome **Giorgi**.  
  
2.  Digitare il nome **Anderson**, quindi premere INVIO.  
  
#### <a name="to-modify-a-column-header"></a>Per modificare un'intestazione di colonna  
  
1.  Fare clic sulla cella che contiene l'intestazione di colonna **LastName**.  
  
2.  Tipo **cognome**, tra cui uno spazio tra le due parole e quindi premere INVIO.  
  
#### <a name="to-save-data"></a>Per salvare i dati  
  
1.  Fare clic su **salvare** nel foglio di lavoro.  
  
2.  Uscire da Excel. Fare clic su **n** quando viene richiesto di salvare le modifiche apportate.  
  
3.  Premere F5 per eseguire nuovamente il progetto.  
  
     Il controllo ListObject con dati di **dipendenti** tabella.  
  
4.  Si noti che il nome nella cella **B7** è ancora **Anderson**, ovvero i dati di modifica apportate e salvate nel database. L'intestazione di colonna **LastName** è stato modificato al formato originale senza spazio, poiché l'intestazione di colonna non è associato al database e si non salvare le modifiche apportate al foglio di lavoro.  
  
#### <a name="to-add-new-rows"></a>Per aggiungere nuove righe  
  
1.  Selezionare una cella all'interno dell'oggetto elenco.  
  
     Verrà visualizzata una nuova riga nella parte inferiore dell'elenco, con un asterisco (**\***) nella prima cella della nuova riga.  
  
2.  Aggiungere le informazioni seguenti nella riga vuota.  
  
    |EmployeeID|LastName|FirstName|Titolo|  
    |----------------|--------------|---------------|-----------|  
    |10|Greco|Mario|Responsabile vendite|  
  
#### <a name="to-delete-rows"></a>Per eliminare righe  
  
-   Fare doppio clic su numero 16 (riga 16) all'estremità sinistra del foglio di lavoro e quindi fare clic su **eliminare**.  
  
#### <a name="to-sort-the-rows-in-the-list"></a>Per ordinare le righe nell'elenco  
  
1.  Selezionare una cella all'interno dell'elenco.  
  
     I pulsanti freccia vengono visualizzati in ogni intestazione di colonna.  
  
2.  Fare clic sul pulsante freccia di **cognome** intestazione di colonna.  
  
3.  Fare clic su **ordinamento crescente**.  
  
     Le righe vengono ordinate in ordine alfabetico in base al cognome.  
  
#### <a name="to-filter-information"></a>Per filtrare le informazioni  
  
1.  Selezionare una cella all'interno dell'elenco.  
  
2.  Fare clic sul pulsante freccia di **titolo** intestazione di colonna.  
  
3.  Fare clic su **rappresentante di vendita**.  
  
     L'elenco Mostra solo le righe che contengono **addetto alle vendite** nel **titolo** colonna.  
  
4.  Fare clic sul pulsante freccia di **titolo** nuovamente l'intestazione di colonna.  
  
5.  Fare clic su **(tutti)**.  
  
     Il filtro viene rimosso e tutte le righe vengono visualizzati.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni fondamentali sull'associazione di una tabella in un database a un oggetto elenco. Ecco alcune possibili attività successive:  
  
-   I dati nella cache in modo che possa essere usata offline. Per ulteriori informazioni, vedere [procedura: memorizzare i dati per l'utilizzo Offline o in un Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Distribuire la soluzione. Per ulteriori informazioni, vedere [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Creare una relazione master/dettaglio tra un campo e una tabella. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di una relazione di dettaglio Master utilizzando un set di dati memorizzati nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Procedura dettagliata: data binding semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  