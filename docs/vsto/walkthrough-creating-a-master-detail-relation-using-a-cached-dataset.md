---
title: 'Procedura dettagliata: Creazione di una relazione di dettaglio Master utilizzando un set di dati memorizzati nella cache | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: abe0b766214c1906afcf443c23948c492a6bde90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>Procedura dettagliata: Creazione di una relazione di dettaglio Master utilizzando un set di dati memorizzati nella cache
  Questa procedura dettagliata illustra la creazione di una relazione master/dettaglio in un foglio di lavoro e la memorizzazione nella cache i dati in modo che la soluzione possa essere usata offline.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere controlli a un foglio di lavoro.  
  
-   Configurare un set di dati da memorizzare nella cache in un foglio di lavoro.  
  
-   Aggiungere il codice per abilitare lo scorrimento di record.  
  
-   Testare il progetto.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso al database di esempio Northwind di SQL Server. Il database può essere nel computer di sviluppo o in un server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Master-Detail**, utilizzando Visual Basic o c#. Assicurarsi che **creare un nuovo documento** è selezionata. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **My Master-Detail** progetto **Esplora**.  
  
## <a name="creating-the-data-source"></a>Creazione dell'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Se la finestra **Origini dati** non è visibile, visualizzarla scegliendo **Visualizza**, **Altre finestre**e **Origini dati**dalla barra dei menu.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e quindi fare clic su **Avanti**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind, o aggiungere una nuova connessione utilizzando il **nuova connessione** pulsante.  
  
5.  Dopo aver selezionato o la creazione di una connessione, fare clic su **Avanti**.  
  
6.  Deselezionare l'opzione per salvare la connessione se è selezionata, quindi scegliere **Avanti**.  
  
7.  Espandere il **tabelle** nodo il **oggetti di Database** finestra.  
  
8.  Selezionare il **ordini** tabella e **Order Details** tabella.  
  
9. Scegliere **Fine**.  
  
 La procedura guidata aggiungerà le due tabelle per il **origini dati** finestra. Aggiunge un dataset tipizzato al progetto che è visibile in **Esplora**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Aggiunta di controlli al foglio di lavoro  
 In questo passaggio si aggiungerà un intervallo denominato, un oggetto elenco e due pulsanti per il primo foglio di lavoro. Innanzitutto, aggiungere l'intervallo denominato e l'oggetto elenco dal **origini dati** finestra in modo che vengono associati automaticamente all'origine dati. Successivamente, aggiungere i pulsanti dal **della casella degli strumenti**.  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>Per aggiungere un intervallo denominato e un oggetto elenco  
  
1.  Verificare che il **My Master-Detail.xlsx** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.  
  
2.  Aprire il **origini dati** finestra ed espandere il **ordini** nodo.  
  
3.  Selezionare il **OrderID** colonna e quindi fare clic sulla freccia giù visualizzata.  
  
4.  Fare clic su **NamedRange** nell'elenco a discesa, quindi trascinare il **OrderID** colonna alla cella **A2**.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `OrderIDNamedRange` viene creato nella cella **A2**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `OrdersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> istanza vengono aggiunti al progetto. Il controllo è associato al <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato il <xref:System.Data.DataSet> istanza.  
  
5.  Scorrere verso il basso oltre le colonne che sono sotto il **ordini** tabella. Nella parte inferiore dell'elenco è il **Order Details** tabella; è qui perché è un elemento figlio del **ordini** tabella. Selezionare questa opzione **Order Details** tabella, non quello allo stesso livello di **ordini** tabella e quindi fare clic sulla freccia giù visualizzata.  
  
6.  Fare clic su **ListObject** nell'elenco a discesa, quindi trascinare il **OrderDetails** alla cella **A6**.  
  
7.  A <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato **Order_DetailsListObject** viene creato nella cella **A6**e associare il <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-two-buttons"></a>Per aggiungere due pulsanti  
  
1.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **A3** del foglio di lavoro.  
  
     Questo pulsante era denominato `Button1`.  
  
2.  Aggiungere un altro <xref:System.Windows.Forms.Button> controllo alla cella **B3** del foglio di lavoro.  
  
     Questo pulsante era denominato `Button2`.  
  
 Successivamente, contrassegnare il set di dati da memorizzare nella cache del documento.  
  
## <a name="caching-the-dataset"></a>La memorizzazione nella cache il set di dati  
 Contrassegnare il set di dati da memorizzare nella cache del documento, eseguendo il set di dati pubblici e l'impostazione di **CacheInDocument** proprietà.  
  
#### <a name="to-cache-the-dataset"></a>Per memorizzare nella cache il set di dati  
  
1.  Selezionare **NorthwindDataSet** nella barra dei componenti.  
  
2.  Nel **proprietà** finestra, modifica il **modificatori** proprietà **pubblica**.  
  
     Set di dati devono essere pubblici prima di abilitare la memorizzazione nella cache.  
  
3.  Modifica il **CacheInDocument** proprietà **True**.  
  
 Il passaggio successivo consiste nella aggiungere testo ai pulsanti e in c# aggiungere il codice per associare i gestori di eventi.  
  
## <a name="initializing-the-controls"></a>Inizializzazione dei controlli  
 Impostare il testo del pulsante e aggiungere i gestori eventi durante il <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> evento.  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>Per inizializzare i dati e i controlli  
  
1.  In **Esplora**, fare doppio clic su **Sheet1. vb** o **Sheet1. cs**, quindi fare clic su **Visualizza codice** nel menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il `Sheet1_Startup` per impostare il testo dei pulsanti.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Solo per c#, aggiungere gestori per il pulsante eventi click per il `Sheet1_Startup` metodo.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Aggiungere il codice per abilitare lo scorrimento di record  
 Aggiungere codice per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento di ogni pulsante per spostarsi tra i record.  
  
#### <a name="to-scroll-through-the-records"></a>Per scorrere i record  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento di `Button1`e aggiungere il codice per spostarsi all'indietro tra i record seguente:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento di `Button2`e aggiungere il codice per passare tra i record seguente:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che i dati vengono visualizzati come previsto e che è possibile usare la soluzione non in linea.  
  
#### <a name="to-test-the-data-caching"></a>Per testare la memorizzazione nella cache di dati  
  
1.  Premere **F5**.  
  
2.  Verificare che l'intervallo denominato e l'oggetto elenco vengono riempiti con i dati dall'origine dati.  
  
3.  Scorrere alcuni record facendo clic sui pulsanti.  
  
4.  Salvare la cartella di lavoro e quindi chiudere la cartella di lavoro e Visual Studio.  
  
5.  Disabilitare la connessione al database. Scollegare il cavo di rete dal computer, se il database si trova in un server o arrestare il servizio SQL Server se il database nel computer di sviluppo.  
  
6.  Aprire Excel e quindi aprire **My Master-Detail.xlsx** dalla directory \bin (\My Master-Detail\bin in Visual Basic o \My Master-Detail\bin\debug in c#).  
  
7.  Scorrere alcuni record per verificare che il foglio di lavoro viene eseguito in genere quando si è disconnessi.  
  
8.  Riconnettersi al database. Connettere nuovamente il computer alla rete se il database si trova in un server o avviare il servizio SQL Server se il database nel computer di sviluppo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base della creazione di una relazione tra dati master/dettaglio in un foglio di lavoro e la memorizzazione nella cache un set di dati. Ecco alcune possibili attività successive:  
  
-   Distribuire la soluzione. Per altre informazioni, vedere [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [La memorizzazione nella cache di dati](../vsto/caching-data.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  