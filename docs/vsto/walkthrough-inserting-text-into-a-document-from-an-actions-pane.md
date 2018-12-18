---
title: 'Procedura dettagliata: Inserimento di testo in un documento da un riquadro azioni | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e562f66dd43b4adc45727c8de1457a24ddf97b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>Procedura dettagliata: inserimento di testo in un documento da un riquadro azioni
  Questa procedura dettagliata viene illustrato come creare un riquadro azioni in un documento di Microsoft Office Word. Nel riquadro azioni contiene due controlli per la raccolta di input e quindi inviano il testo al documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Progettazione di un'interfaccia per l'utilizzo di controlli Windows Form in un controllo riquadro azioni.  
  
-   Visualizzazione del riquadro azioni all'apertura dell'applicazione.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome **My Basic Actions Pane**. Nella procedura guidata, selezionare **creare un nuovo documento**. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Basic Actions Pane** progetto **Esplora**.  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>Aggiunta di testo e i segnalibri nel documento  
 Nel riquadro azioni invierà testo ai segnalibri nel documento. Per progettare il documento, digitare del testo per creare un form di base.  
  
#### <a name="to-add-text-to-your-document"></a>Per aggiungere testo al documento  
  
1.  Nel documento di Word, digitare il testo seguente:  
  
     **21 marzo 2008**  
  
     **Name**  
  
     **Indirizzo**  
  
     **Questo è un esempio di un riquadro azioni di base in Word.**  
  
 È possibile aggiungere un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento trascinandolo dal **della casella degli strumenti** in Visual Studio o utilizzando il **segnalibro** nella finestra di dialogo di Word.  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>Per aggiungere un controllo Bookmark a un documento  
  
1.  Dal **controlli Word** scheda della finestra il **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento.  
  
     Il **Aggiungi controllo Bookmark** viene visualizzata la finestra di dialogo.  
  
2.  Selezionare la parola **nome**, senza selezionare il segno di paragrafo e fare clic su **OK**.  
  
    > [!NOTE]  
    >  Il segnalibro deve essere il segno di paragrafo. Se i segni di paragrafo non sono visibili nel documento, fare clic su di **strumenti** dal menu **strumenti di Microsoft Office Word** e quindi fare clic su **opzioni**. Fare clic sul **visualizzazione** scheda e selezionare il **segni di paragrafo** casella di controllo di **formattazione** sezione del **opzioni** la finestra di dialogo.  
  
3.  Nel **proprietà** finestra, modifica il **nome** proprietà di **Bookmark1** a **showName**.  
  
4.  Selezionare la parola **indirizzo**, senza selezionare il segno di paragrafo.  
  
5.  Nel **inserire** scheda della barra multifunzione, nel **collegamenti** gruppo, fare clic su **segnalibro**.  
  
6.  Nel **segnalibro** della finestra di dialogo tipo **showAddress** nel **nome del segnalibro** casella e fare clic su **Aggiungi**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Aggiunta di controlli al riquadro azioni  
 Per progettare l'interfaccia del riquadro azioni, aggiungere un controllo riquadro azioni al progetto e quindi aggiungere controlli Windows Form al controllo del riquadro azioni.  
  
#### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni  
  
1.  Selezionare il **My Basic Actions Pane** nel progetto **Esplora**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** la finestra di dialogo, fare clic su **controllo riquadro azioni**, denominare il controllo **InsertTextControl** e fare clic su **Aggiungi**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Per aggiungere controlli Windows Form al controllo riquadro azioni  
  
1.  Se il controllo riquadro azioni non è visibile nella finestra di progettazione, fare doppio clic su **InsertTextControl**.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare un **etichetta** nel controllo riquadro azioni.  
  
3.  Modifica il **testo** proprietà del controllo etichetta a **nome**.  
  
4.  Aggiungere un **Textbox** al controllo del riquadro azioni e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**GetName**|  
    |**Dimensione**|**130, 20**|  
  
5.  Aggiungere un secondo **etichetta** al controllo del riquadro azioni e modificare il **testo** proprietà **indirizzo**.  
  
6.  Aggiungere un secondo **Textbox** al controllo del riquadro azioni e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**GetAddress**|  
    |**Accetta restituito**|**True**|  
    |**Multiline**|**True**|  
    |**Dimensione**|**130, 40**|  
  
7.  Aggiungere un **pulsante** al controllo del riquadro azioni e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**addText**|  
    |**per**|**Inserisci**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>Aggiungere il codice per inserire il testo nel documento  
 Nel riquadro azioni, scrivere codice che inserisce il testo delle caselle di testo appropriato <xref:Microsoft.Office.Tools.Word.Bookmark> controlli nel documento. È possibile utilizzare la `Globals` classe per accedere ai controlli nel documento dai controlli nel riquadro azioni. Per ulteriori informazioni, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Per inserire il testo nel riquadro azioni in un segnalibro nel documento  
  
1.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del **addText** pulsante.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  In c#, è necessario aggiungere un gestore eventi per il clic del pulsante. È possibile inserire il codice nel `InsertTextControl` costruttore dopo la chiamata a `IntializeComponent`. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>Aggiungere il codice per visualizzare il riquadro azioni  
 Per visualizzare il riquadro azioni, aggiungere il controllo creato per la raccolta di controllo.  
  
#### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni  
  
1.  Creare una nuova istanza del controllo del riquadro azioni nel `ThisDocument` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Aggiungere il codice seguente per il <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore dell'evento di `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 Testare il documento per verificare che il riquadro azioni viene visualizzata quando il documento viene aperto e che il testo digitato nelle caselle di testo viene inserito nei segnalibri quando si fa clic sul pulsante.  
  
#### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il riquadro azioni è visibile.  
  
3.  Digitare il nome e indirizzo nelle caselle di testo nel riquadro azioni, fare clic su **inserire**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Ecco alcune possibili attività successive:  
  
-   Creazione di un riquadro azioni in Excel. Per ulteriori informazioni, vedere [procedura: aggiungere un riquadro azioni a cartelle di lavoro di Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Associazione dati a controlli in un riquadro azioni. Per ulteriori informazioni, vedere [procedura dettagliata: associazione di dati a controlli in un riquadro azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro azioni a cartelle di lavoro di Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Procedura: gestire il Layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Controllo Bookmark](../vsto/bookmark-control.md)  
  
  