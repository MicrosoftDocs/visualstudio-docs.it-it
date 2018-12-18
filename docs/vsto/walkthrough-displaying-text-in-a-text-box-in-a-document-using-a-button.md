---
title: 'Procedura dettagliata: Visualizzazione di testo in una casella di testo in un documento mediante un pulsante | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 086137debfa35cb08dfa3b315208ce3686d74153
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button"></a>Procedura dettagliata: visualizzazione di testo in una casella di testo di un documento tramite un pulsante
  Questa procedura dettagliata illustra come usare i pulsanti e le caselle di testo in una personalizzazione a livello di documento per Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di controlli al documento di Word in un progetto a livello di documento in fase di progettazione.  
  
-   Popolamento di una casella di testo quando si fa clic su un pulsante.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome **My Word Button**. Nella procedura guidata, selezionare **creare un nuovo documento**.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Word Button** progetto **Esplora**.  
  
## <a name="adding-controls-to-the-word-document"></a>Aggiunta di controlli al documento di Word  
 I controlli dell'interfaccia utente sono costituiti da un pulsante e da una casella di testo nel documento di Word.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo  
  
1.  Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Word.Controls.TextBox> controllo al documento.  
  
    > [!NOTE]  
    >  In Word i controlli vengono rilasciati in linea con il testo per impostazione predefinita. È possibile modificare la funzionalità dei controlli e oggetti forma sono inseriti modificando il valore predefinito nel **modifica** scheda della finestra di **opzioni** nella finestra di dialogo di Word.  
  
3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.  
  
4.  Trovare **TextBox1** nel **proprietà** casella di riepilogo a discesa finestra e modificare il **nome** proprietà della casella di testo per **displayText**.  
  
5.  Trascinare un **pulsante** al documento e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**per**|**Inserire il testo**|  
  
 È ora possibile scrivere il codice che verrà eseguito quando si fa clic sul pulsante.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Popolamento della casella di testo quando si fa clic sul pulsante  
 Ogni volta che l'utente fa clic sul pulsante, **Hello World!** viene aggiunto alla casella di testo.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante  
  
1.  In **Esplora**, fare doppio clic su **ThisDocument**, quindi fare clic su **Visualizza codice** nel menu di scelta rapida.  
  
2.  Aggiungere il codice seguente al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  In C# è necessario aggiungere un gestore eventi per il pulsante all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare il documento, per assicurarsi che il messaggio **Hello World!** Quando si fa clic sul pulsante, viene visualizzato nella casella di testo.  
  
#### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Fare clic sul pulsante.  
  
3.  Verificare che **Hello World!** viene visualizzato nella casella di testo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra i concetti di base relativi all'uso di pulsanti e caselle di testo nei documenti di Word. Ecco alcune possibili attività successive:  
  
-   Uso di una casella combinata per modificare la formattazione. Per ulteriori informazioni, vedere [procedura dettagliata: Modifica documento formattazione mediante controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Uso di pulsanti di opzione per selezionare gli stili del grafico. Per ulteriori informazioni, vedere [procedura dettagliata: aggiornamento di un grafico in un documento mediante pulsanti](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  