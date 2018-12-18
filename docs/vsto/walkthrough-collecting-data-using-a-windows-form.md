---
title: 'Procedura dettagliata: Raccolta dati utilizzando un Windows Form | Documenti Microsoft'
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
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2c6945d4e44a0ecb56c6ae7a3823dc0d7951f197
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-collecting-data-using-a-windows-form"></a>Procedura dettagliata: raccolta di dati tramite Windows Form
  Questa procedura dettagliata spiega come aprire un Windows Form da una personalizzazione a livello di documento per Microsoft Office Excel, raccogliere le informazioni dall'utente e scriverle in una cella del foglio di lavoro.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Nonostante in questa procedura dettagliata venga usato un progetto a livello di documento in modo specifico per Excel, i concetti illustrati sono applicabili ad altri progetti di Office.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto  
 Il primo passaggio consiste nella creazione di un progetto Cartella di lavoro di Excel.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto relativo a una cartella di lavoro di Excel denominato **WinFormInput**e selezionare **Crea un nuovo documento** nella procedura guidata. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro di Excel viene aperta nella finestra di progettazione di Visual Studio e il progetto **WinFormInput** viene aggiunto in **Esplora soluzioni**.  
  
## <a name="adding-a-namedrange-control-to-the-worksheet"></a>Aggiunta di un controllo NamedRange al foglio di lavoro  
  
#### <a name="to-add-a-named-range-to-sheet1"></a>Per aggiungere un intervallo denominato a Sheet1  
  
1.  Selezionare la cella **A1** in `Sheet1`.  
  
2.  Nella casella **Nome** digitare **formInput**.  
  
     La casella **Nome** si trova a sinistra della barra della formula, sopra la colonna **A** del foglio di lavoro.  
  
3.  Premere INVIO.  
  
     Un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> viene aggiunto nella cella **A1**. Sul foglio di lavoro non sono presenti indicazioni visibili, ma nella casella **Nome** (al di sotto del foglio di lavoro sul lato sinistro) e nella finestra **Proprietà** viene visualizzato **formInput** quando la cella **A1** viene selezionata.  
  
## <a name="adding-a-windows-form-to-the-project"></a>Aggiunta di Windows Form al progetto  
 Creare un controllo Windows Form per richiedere informazioni all'utente.  
  
#### <a name="to-add-a-windows-form"></a>Per aggiungere un controllo Windows Form  
  
1.  Selezionare il progetto **WinFormInput** in **Esplora soluzioni**.  
  
2.  Scegliere **Aggiungi Windows Form** dal menu **Progetto**.  
  
3.  Assegnare al modulo il nome **GetInputString.vb** o **GetInputString.cs**, quindi scegliere **Aggiungi**.  
  
     Il nuovo modulo verrà aperto nella finestra di progettazione.  
  
4.  Aggiungere al modulo una classe <xref:System.Windows.Forms.TextBox> e una classe <xref:System.Windows.Forms.Button> .  
  
5.  Scegliere il pulsante, trovare la proprietà **Text** nella finestra **Proprietà** , quindi modificare il testo in **OK**.  
  
 Aggiungere quindi codice a `ThisWorkbook.vb` o `ThisWorkbook.cs` per raccogliere le informazioni relative all'utente.  
  
## <a name="displaying-the-windows-form-and-collecting-information"></a>Visualizzazione di Windows Form e raccolta di informazioni  
 Creare un'istanza del controllo Windows Form `GetInputString` e visualizzarla, quindi scrivere le informazioni relative all'utente in una cella del foglio di lavoro.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Per visualizzare il modulo e raccogliere informazioni  
  
1.  Fare clic con il pulsante destro del mouse su **ThisWorkbook.vb** o **ThisWorkbook.cs** in **Esplora soluzioni**e selezionare **Visualizza codice**.  
  
2.  Nel gestore dell'evento <xref:Microsoft.Office.Tools.Excel.Workbook.Open> di `ThisWorkbook`, aggiungere il codice riportato di seguito per dichiarare una variabile per il modulo `GetInputString` e visualizzare il modulo.  
  
    > [!NOTE]  
    >  In C# è necessario aggiungere un gestore dell'evento, come mostrato nell'evento <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> che segue. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3.  Creare un metodo denominato `WriteStringToCell` , che consente di scrivere testo in un intervallo denominato. Tale metodo viene chiamato dal modulo e l'input utente viene passato al controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> , `formInput`, posizionato sulla cella **A1**.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
 Aggiungere quindi al modulo il codice per la gestione dell'evento Click del pulsante.  
  
## <a name="sending-information-to-the-worksheet"></a>Invio di informazioni al foglio di lavoro  
  
#### <a name="to-send-information-to-the-worksheet"></a>Per inviare informazioni al foglio di lavoro  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **GetInputString**, quindi scegliere **Progettazione visualizzazioni**.  
  
2.  Fare doppio clic sul pulsante per aprire il file di codice contenente il gestore dell'evento <xref:System.Windows.Forms.Control.Click> del pulsante aggiunto.  
  
3.  Aggiungere il codice al gestore dell'evento per estrarre l'input dalla casella di testo, inviarlo alla funzione `WriteStringToCell`, quindi chiudere il modulo.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="testing"></a>Test  
 È ora possibile eseguire il progetto. Windows Form viene visualizzato e l'input è presente nel foglio di lavoro.  
  
#### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il controllo Windows Form venga visualizzato.  
  
3.  Digitare **Hello World** nella casella di testo e fare clic su **OK**.  
  
4.  Assicurarsi che il testo **Hello World** sia visualizzato nella cella **A1** del foglio di lavoro.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata fornisce le informazioni di base sulla visualizzazione di un controllo Windows Form e sul passaggio di dati a un foglio di lavoro. Altre attività che è possibile eseguire includono:  
  
-   Usare i controlli Windows Form in una cartella di lavoro di Excel o un documento di Word. Per altre informazioni, vedere [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Modificare l'interfaccia utente di un'applicazione di Microsoft Office da una personalizzazione a livello di documento o un componente aggiuntivo VSTO a livello di applicazione. Per ulteriori informazioni, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)  
  
  