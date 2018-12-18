---
title: 'Procedura dettagliata: Data Binding semplice in un progetto a livello di documento | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95029c946939bf0918e15034625ad31c1e5897b9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Procedura dettagliata: associazione di dati semplice in un progetto a livello di documento
  Questa procedura dettagliata illustra le nozioni di base del data binding in un progetto a livello di documento. Un singolo campo dati in un database di SQL Server è associato a un intervallo denominato in Microsoft Office Excel. La procedura dettagliata illustra inoltre come aggiungere controlli che consentono di scorrere tutti i record nella tabella.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un'origine dati per un progetto di Excel.  
  
-   Aggiunta di controlli a un foglio di lavoro.  
  
-   Scorrimento di record del database.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server con il database di esempio Northwind di SQL Server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto di cartella di lavoro di Excel con il nome **My Simple Data Binding**, utilizzando Visual Basic o c#. Assicurarsi che **creare un nuovo documento** è selezionata. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **My Simple Data Binding** progetto **Esplora**.  
  
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
  
8.  Selezionare la casella di controllo accanto al **clienti** tabella.  
  
9. Scegliere **Fine**.  
  
 La procedura guidata aggiunge il **clienti** tabella il **origini dati** finestra. Aggiunge un dataset tipizzato al progetto che è visibile in **Esplora**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Aggiunta di controlli al foglio di lavoro  
 Questa procedura dettagliata, sono necessari due intervalli denominati e quattro pulsanti presenti nel primo foglio di lavoro. Aggiungere innanzitutto i due intervalli denominati dal **origini dati** finestra in modo che vengono associati automaticamente all'origine dati. Successivamente, aggiungere i pulsanti dal **della casella degli strumenti**.  
  
#### <a name="to-add-two-named-ranges"></a>Per aggiungere due intervalli denominati  
  
1.  Verificare che il **My Binding.xlsx dati semplice** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con **Sheet1** visualizzato.  
  
2.  Aprire il **origini dati** finestra ed espandere il **clienti** nodo.  
  
3.  Selezionare il **CompanyName** colonna e quindi fare clic sulla freccia giù visualizzata.  
  
4.  Selezionare **NamedRange** nell'elenco a discesa, quindi trascinare il **CompanyName** colonna alla cella **A1**.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `companyNameNamedRange` viene creato nella cella **A1**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `customersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> istanza vengono aggiunti al progetto. Il controllo è associato al <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato il <xref:System.Data.DataSet> istanza.  
  
5.  Selezionare il **CustomerID** colonna il **origini dati** finestra e quindi fare clic sulla freccia giù visualizzata.  
  
6.  Fare clic su **NamedRange** nell'elenco a discesa, quindi trascinare il **CustomerID** colonna alla cella **B1**.  
  
7.  Un altro <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `customerIDNamedRange` viene creato nella cella **B1**e associare il <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-four-buttons"></a>Per aggiungere quattro pulsanti  
  
1.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un <xref:System.Windows.Forms.Button> controllo alla cella **A3** del foglio di lavoro.  
  
     Questo pulsante era denominato `Button1`.  
  
2.  Aggiungere altri tre pulsanti per le celle seguenti nell'ordine indicato, in modo che i nomi vengono visualizzati:  
  
    |Cella|(Nome)|  
    |----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 Il passaggio successivo consiste nella aggiungere testo ai pulsanti e in c# aggiungere gestori eventi.  
  
## <a name="initializing-the-controls"></a>Inizializzazione dei controlli  
 Impostare il testo del pulsante e aggiungere i gestori eventi durante il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento.  
  
#### <a name="to-initialize-the-controls"></a>Per inizializzare i controlli  
  
1.  In **Esplora**, fare doppio clic su **Sheet1. vb** o **Sheet1. cs**, quindi fare clic su **Visualizza codice** nel menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il `Sheet1_Startup` per impostare il testo per ogni pulsante.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3.  Solo per c#, aggiungere gestori per il pulsante eventi click per il `Sheet1_Startup` metodo.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
 A questo punto aggiungere il codice per gestire il <xref:System.Windows.Forms.Control.Click> eventi dei pulsanti in modo che l'utente può scorrere i record.  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Aggiungere il codice per abilitare lo scorrimento di record  
 Aggiungere codice per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento di ogni pulsante per spostarsi tra i record.  
  
#### <a name="to-move-to-the-first-record"></a>Per spostare il primo record  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento del `Button1` pulsante e aggiungere il codice seguente per spostare il primo record:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
#### <a name="to-move-to-the-previous-record"></a>Per passare al record precedente  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento del `Button2` pulsante e aggiungere il codice seguente per riportare la posizione di uno:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
#### <a name="to-move-to-the-next-record"></a>Per spostarsi al record successivo  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento del `Button3` pulsante e aggiungere il codice seguente per spostare la posizione di uno:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
#### <a name="to-move-to-the-last-record"></a>Per spostarsi all'ultimo record  
  
1.  Aggiungere un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento del `Button4` pulsante e aggiungere il codice seguente per spostarsi all'ultimo record:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che è possibile esplorare i record nel database.  
  
#### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il primo record visualizzato nelle celle **A1** e **B1**.  
  
3.  Fare clic su di  **>**  (`Button3`) pulsante e verificare che il record successivo nella cella **A1** e **B1**.  
  
4.  Fare clic sugli altri pulsanti di scorrimento per verificare che il record sia stato modificato nel modo previsto.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni fondamentali sull'associazione di un intervallo denominato a un campo in un database. Ecco alcune possibili attività successive:  
  
-   I dati nella cache in modo che possa essere usata offline. Per ulteriori informazioni, vedere [procedura: memorizzare i dati per l'utilizzo Offline o in un Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Associazione di celle a più colonne in una tabella, anziché a un campo. Per ulteriori informazioni, vedere [procedura dettagliata: Data Binding complesso in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Utilizzare un <xref:System.Windows.Forms.BindingNavigator> scorrere i record di controllo. Per ulteriori informazioni, vedere [procedura: passare dati con il controllo BindingNavigator Windows Form](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Procedura dettagliata: data binding complesso in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  