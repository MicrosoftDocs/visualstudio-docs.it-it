---
title: 'Procedura dettagliata: Aggiornamento di un grafico in un documento mediante pulsanti di opzione | Documenti Microsoft'
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
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1f1340c3e67ca0647448228fb2414fa4ba7d4003
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-updating-a-chart-in-a-document-using-radio-buttons"></a>Procedura dettagliata: aggiornamento di un grafico in un documento mediante pulsanti di opzione
  Questa procedura dettagliata illustra come usare i pulsanti di opzione in una personalizzazione a livello di documento per Microsoft Office Word, per consentire agli utenti di selezionare stili del grafico nel documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di un grafico al documento di un progetto a livello di documento in fase di progettazione.  
  
-   Raggruppamento dei pulsanti di opzione aggiungendoli a un controllo utente.  
  
-   Modifica dello stile del grafico quando si seleziona un'opzione.  
  
 Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli di Word in [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome **My Chart Options**. Nella procedura guidata, selezionare **creare un nuovo documento**. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Chart Options** progetto **Esplora**.  
  
## <a name="adding-a-chart-to-the-document"></a>Aggiunta di un grafico al documento  
  
#### <a name="to-add-a-chart"></a>Per aggiungere un grafico  
  
1.  Nel documento di Word ospitato nella finestra di progettazione di Visual Studio, sulla barra multifunzione, fare clic su di **inserire** scheda.  
  
2.  Nel **testo** gruppo, fare clic su di **Inserisci oggetto** pulsante a discesa e fare clic su **oggetto**.  
  
     Il **oggetto** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo di oggetto** elenco il **Crea nuovo** , selezionare **grafico Microsoft** e quindi fare clic su **OK**.  
  
     Un grafico verrà aggiunto al documento nel punto di inserimento e **foglio dati** verrà visualizzata la finestra con alcuni dati predefiniti.  
  
4.  Chiudi il **foglio dati** finestra per accettare i valori predefiniti nel grafico e fare clic all'interno del documento per spostare lo stato attivo fuori del grafico.  
  
5.  Il pulsante destro del grafico e quindi fare clic su **formato oggetto**.  
  
6.  Nel **Layout** scheda della finestra il **formato oggetto** nella finestra di dialogo **quadrato** e fare clic su **OK**.  
  
## <a name="adding-a-user-control-to-the-project"></a>Aggiunta di un controllo utente al progetto  
 I pulsanti di opzione in un documento non si escludono a vicenda per impostazione predefinita. È possibile farli funzionare correttamente aggiungendoli a un controllo utente e quindi scrivendo il codice per controllare la selezione.  
  
#### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente  
  
1.  Selezionare il **My Chart Options** nel progetto **Esplora**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** la finestra di dialogo, fare clic su **controllo utente**, denominare il controllo **ChartOptions** e fare clic su **Aggiungi**.  
  
#### <a name="to-add-windows-form-controls-to-the-user-control"></a>Per aggiungere controlli Windows Form al controllo utente  
  
1.  Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic su **ChartOptions** in **Esplora**.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare il primo **pulsante di opzione** al controllo utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**Istogramma**|  
    |**per**|**Istogramma**|  
  
3.  Aggiungere un secondo **pulsante di opzione** all'utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**per**|**Grafico a barre**|  
  
4.  Aggiungere un terzo **pulsante di opzione** all'utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**per**|**Grafico a linee**|  
  
5.  Aggiungere un quarto **pulsante di opzione** all'utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**opzione areaBlockChart**|  
    |**per**|**Grafico ad area**|  
  
## <a name="adding-references"></a>Aggiunta di riferimenti  
 Per accedere al grafico dal controllo utente in un documento, è necessario avere un riferimento all'assembly Microsoft.Office.Interop.Graph nel progetto.  
  
#### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Per aggiungere un riferimento all'assembly Microsoft.Office.Interop.Graph  
  
1.  Scegliere **Aggiungi riferimento** dal menu **Progetto**.  
  
     Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.  
  
2.  Nel **.NET** , selezionare **Microsoft.Office.Interop.Graph** e fare clic su **OK**. Selezionare la versione 14.0.0.0 dell'assembly.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Modifica dello stile del grafico quando si seleziona un pulsante di opzione  
 Per far funzionare i pulsanti correttamente, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare una routine per l'evento `CheckedChanged` di ogni pulsante di opzione.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Per creare un evento e una proprietà in un controllo utente  
  
1.  In **Esplora**, fare il controllo utente e quindi fare clic su **Visualizza codice**.  
  
2.  Aggiungere il codice per creare un evento `SelectionChanged` e la proprietà `Selection` nella classe `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
#### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Per gestire l'evento CheckedChange dei pulsanti di opzione  
  
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
  
## <a name="adding-the-user-control-to-the-document"></a>Aggiunta del controllo utente al documento  
 Quando si compila la soluzione, il nuovo controllo utente viene automaticamente aggiunto per il **della casella degli strumenti**. È quindi possibile trascinare il controllo di **della casella degli strumenti** al documento.  
  
#### <a name="to-add-the-user-control-your-document"></a>Per aggiungere il controllo utente al documento  
  
1.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il **ChartOptions** controllo utente viene aggiunto per il **della casella degli strumenti**.  
  
2.  In **Esplora**, fare doppio clic su **ThisDocument. vb** o **ThisDocument. cs**, quindi fare clic su **Visualizza finestra di progettazione**.  
  
3.  Trascinare il `ChartOptions` controllo il **della casella degli strumenti** al documento.  
  
     Nel **proprietà** finestra, il nome del controllo che è stato aggiunto al documento `ChartOptions1`.  
  
## <a name="changing-the-chart-type"></a>Modifica del tipo di grafico  
 Creare un gestore eventi per modificare il tipo di grafico in base all'opzione selezionata nel controllo utente.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Per modificare il tipo di grafico visualizzato nel documento  
  
1.  Aggiungere il seguente gestore eventi alla classe `ThisDocument`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  In C# è necessario aggiungere un gestore eventi per il controllo utente all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 A questo punto è possibile testare il documento per accertarsi che lo stile del grafico sia aggiornato correttamente quando si seleziona un pulsante di opzione.  
  
#### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare vari pulsanti di opzione.  
  
3.  Verificare che lo stile del grafico sia modificato in base alla selezione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Ecco alcune possibili attività successive:  
  
-   Usare un pulsante per popolare una casella di testo. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione del testo in una casella di testo in un documento mediante un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Modificare la formattazione selezionando uno stile da una casella combinata. Per ulteriori informazioni, vedere [procedura dettagliata: Modifica documento formattazione mediante controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate ed esempi di sviluppo di office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  