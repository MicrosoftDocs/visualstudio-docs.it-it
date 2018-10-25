---
title: 'Procedura dettagliata: Aggiornamento di un grafico in un documento mediante pulsanti di opzione'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5e82c50c83a8824b4570779034b0480aa0615a30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904674"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Procedura dettagliata: Aggiornamento di un grafico in un documento mediante pulsanti di opzione
  Questa procedura dettagliata illustra come usare i pulsanti di opzione in una personalizzazione a livello di documento per Microsoft Office Word, per consentire agli utenti di selezionare stili del grafico nel documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
- Aggiunta di un grafico al documento di un progetto a livello di documento in fase di progettazione.  
  
- Raggruppamento dei pulsanti di opzione aggiungendoli a un controllo utente.  
  
- Modifica dello stile del grafico quando si seleziona un'opzione.  
  
  Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli Word all'indirizzo [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Creare il progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome **My Chart Options**. Nella procedura guidata, selezionare **creare un nuovo documento**. Per altre informazioni, vedere [procedura: progetti di Office di creare in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Chart Options** progetto al **Esplora soluzioni**.  
  
## <a name="add-a-chart-to-the-document"></a>Aggiungere un grafico al documento  
  
### <a name="to-add-a-chart"></a>Per aggiungere un grafico  
  
1.  Nel documento di Word ospitato nella finestra di progettazione di Visual Studio, sulla barra multifunzione, scegliere il **Inserisci** scheda.  
  
2.  Nel **testo** gruppo, fare clic sui **Inserisci oggetto** pulsante elenco a discesa e fare clic su **oggetto**.  
  
     Il **oggetto** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo di oggetto** elenco le **Crea nuovo** scheda, seleziona **grafico di Microsoft Graph** e quindi fare clic su **OK**.  
  
     Viene aggiunto un grafico in corrispondenza del punto di inserimento nel documento e il **foglio dati** verrà visualizzata la finestra con alcuni dati predefiniti.  
  
4.  Chiudi il **foglio dati** finestra per accettare i valori predefiniti nel grafico e fare clic all'interno del documento per spostare lo stato attivo fuori del grafico.  
  
5.  Il pulsante destro del grafico e quindi fare clic su **formato oggetto**.  
  
6.  Nel **Layout** scheda della finestra di **oggetto formato** nella finestra di dialogo **quadrato** e fare clic su **OK**.  
  
## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto  
 I pulsanti di opzione in un documento non si escludono a vicenda per impostazione predefinita. È possibile farli funzionare correttamente aggiungendoli a un controllo utente e quindi scrivendo il codice per controllare la selezione.  
  
### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente  
  
1.  Selezionare il **My Chart Options** del progetto nelle **Esplora soluzioni**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** finestra di dialogo, fare clic su **controllo utente**, denominare il controllo **ChartOptions** e fare clic su **Aggiungi**.  
  
### <a name="to-add-windows-form-controls-to-the-user-control"></a>Per aggiungere controlli Windows Form al controllo utente  
  
1.  Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic su **ChartOptions** nelle **Esplora soluzioni**.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare il primo **pulsante di opzione** al controllo utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**Istogramma**|  
    |**per**|**Istogramma a colonne**|  
  
3.  Aggiungere una seconda **pulsante di opzione** all'utente controllare e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**per**|**Grafico a barre**|  
  
4.  Aggiungere un terzo **pulsante di opzione** all'utente controllare e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**per**|**Grafico a linee**|  
  
5.  Aggiungere un quarto **pulsante di opzione** all'utente controllare e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**opzione areaBlockChart**|  
    |**per**|**Grafico ad area**|  
  
## <a name="add-references"></a>Aggiunta di riferimenti  
 Per accedere al grafico dal controllo utente in un documento, è necessario disporre di un riferimento al `Microsoft.Office.Interop.Graph` assembly nel progetto.  
  
### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Per aggiungere un riferimento all'assembly Microsoft.Office.Interop.Graph  
  
1.  Scegliere **Aggiungi riferimento** dal menu **Progetto**.  
  
     Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.  
  
2.  Nel **.NET** scheda, seleziona **Microsoft.Office.Interop.Graph** e fare clic su **OK**. Selezionare la versione 14.0.0.0 dell'assembly.  
  
## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Modificare lo stile del grafico quando viene selezionato un pulsante di opzione  
 Per far funzionare i pulsanti correttamente, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare una routine per l'evento `CheckedChanged` di ogni pulsante di opzione.  
  
### <a name="to-create-an-event-and-property-on-a-user-control"></a>Per creare un evento e una proprietà in un controllo utente  
  
1.  Nelle **Esplora soluzioni**, fare clic sul controllo utente e quindi fare clic su **Visualizza codice**.  
  
2.  Aggiungere il codice per creare un evento `SelectionChanged` e la proprietà `Selection` nella classe `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Per gestire l'evento CheckedChange dei pulsanti di opzione  
  
1.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e quindi generare l'evento.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  In C# è necessario aggiungere gestori eventi per i pulsanti di opzione. È possibile aggiungere questo codice al costruttore `ChartOptions` dopo la chiamata a `InitializeComponent`. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="add-the-user-control-to-the-document"></a>Aggiungere il controllo utente al documento  
 Quando si compila la soluzione, il nuovo controllo utente viene automaticamente aggiunto per il **casella degli strumenti**. È quindi possibile trascinare il controllo dal **casella degli strumenti** al documento.  
  
### <a name="to-add-the-user-control-your-document"></a>Per aggiungere il controllo utente al documento  
  
1.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il **ChartOptions** controllo utente viene aggiunto per il **della casella degli strumenti**.  
  
2.  In **Esplora soluzioni**, fare doppio clic su **ThisDocument. vb** oppure **ThisDocument.cs**, quindi fare clic su **Progettazione viste**.  
  
3.  Trascinare il `ChartOptions` controllare dal **casella degli strumenti** al documento.  
  
     Nel **delle proprietà** finestra, il nome del controllo appena aggiunto al documento `ChartOptions1`.  
  
## <a name="change-the-chart-type"></a>Modificare il tipo di grafico  
 Creare un gestore eventi per modificare il tipo di grafico in base all'opzione selezionata nel controllo utente.  
  
### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Per modificare il tipo di grafico visualizzato nel documento  
  
1.  Aggiungere il seguente gestore eventi alla classe `ThisDocument`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  In C# è necessario aggiungere un gestore eventi per il controllo utente all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 A questo punto è possibile testare il documento per accertarsi che lo stile del grafico sia aggiornato correttamente quando si seleziona un pulsante di opzione.  
  
### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Selezionare vari pulsanti di opzione.  
  
3.  Verificare che lo stile del grafico sia modificato in base alla selezione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Ecco alcune possibili attività successive:  
  
-   Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [procedura dettagliata: visualizzazione di testo in una casella di testo in un documento tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Modificare la formattazione selezionando uno stile da una casella combinata. Per altre informazioni, vedere [procedura dettagliata: modifica la formattazione dei documenti mediante controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  