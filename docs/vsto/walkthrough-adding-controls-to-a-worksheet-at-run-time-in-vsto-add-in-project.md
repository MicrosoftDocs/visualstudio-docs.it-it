---
title: 'Procedura dettagliata: Aggiunta di controlli a un foglio di lavoro in fase di esecuzione in VSTO aggiuntivo progetto | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47c647e2b3af6941f7b4a4d6f28eccfac2b31e2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Procedura dettagliata: Aggiunta di controlli a un foglio di lavoro in fase di esecuzione in un progetto di componente aggiuntivo VSTO
  È possibile aggiungere controlli a qualsiasi foglio di lavoro aperto mediante un componente aggiuntivo VSTO per Excel. Questa procedura dettagliata illustra come usare la barra multifunzione per consentire agli utenti l'aggiunta di oggetti <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro. Per informazioni, vedere [aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Si applica a:** le informazioni contenute in questo argomento sono valide per i progetti di componente aggiuntivo VSTO per Excel. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un'interfaccia utente per l'aggiunta di controlli al foglio di lavoro.  
  
-   Aggiunta di controlli al foglio di lavoro.  
  
-   Rimozione di controlli dal foglio di lavoro.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="creating-a-new-excel-vsto-add-in-project"></a>Creazione di un nuovo progetto di componente aggiuntivo VSTO per Excel  
 Creare innanzitutto un progetto di componente aggiuntivo VSTO per Excel.  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO per Excel  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto di componente aggiuntivo VSTO di Excel con il nome **ExcelDynamicControls**. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Aggiungere un riferimento di **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** assembly. Tale riferimento è necessario per aggiungere a livello di codice un controllo Windows Form al foglio di lavoro più avanti in questa procedura dettagliata.  
  
## <a name="providing-a-ui-to-add-controls-to-a-worksheet"></a>Creazione di un'interfaccia utente per l'aggiunta di controlli a un foglio di lavoro  
 Aggiungere una scheda personalizzata alla barra multifunzione di Excel. Gli utenti possono selezionare caselle di controllo nella scheda per aggiungere i controlli a un foglio di lavoro.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Per creare un'interfaccia utente per l'aggiunta di controlli a un foglio di lavoro  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **della barra multifunzione (finestra di progettazione visiva)**, quindi fare clic su **Aggiungi**.  
  
     Un file denominato **Ribbon1. cs** o **Ribbon1. vb** nella finestra di progettazione della barra multifunzione e visualizza una scheda predefinita e un gruppo.  
  
3.  Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare un controllo casella di controllo **group1**.  
  
4.  Fare clic su **CheckBox1** per selezionarlo.  
  
5.  Nella finestra **Proprietà** modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**Pulsante**|  
    |**Etichetta**|**Pulsante**|  
  
6.  Aggiungere una seconda casella di controllo a **group1**e quindi modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**NamedRange**|  
    |**Etichetta**|**NamedRange**|  
  
7.  Aggiungere una terza casella di controllo per **group1**e quindi modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**ListObject**|  
    |**Etichetta**|**ListObject**|  
  
## <a name="adding-controls-to-the-worksheet"></a>Aggiunta di controlli al foglio di lavoro  
 I controlli gestiti possono essere aggiunti solo a elementi host che fungono da contenitori. Poiché i progetti di componenti aggiuntivi VSTO vengono usati con qualsiasi cartella di lavoro aperta, il componente aggiuntivo VSTO converte il foglio di lavoro in un elemento host oppure ottiene un elemento host esistente, prima di aggiungere il controllo. Aggiungere codice ai gestori di eventi Click di ciascun controllo per generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> basato su un foglio di lavoro aperto. Aggiungere quindi un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.ListObject> alla selezione corrente nel foglio di lavoro.  
  
#### <a name="to-add-controls-to-a-worksheet"></a>Per aggiungere controlli a un foglio di lavoro  
  
1.  Nella finestra di progettazione della barra multifunzione, fare doppio clic su **pulsante**.  
  
     Il <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> gestore dell'evento del **pulsante** casella di controllo viene aperto nell'Editor di codice.  
  
2.  Sostituire il gestore eventi `Button_Click` con il codice seguente.  
  
     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi viene aggiunto un controllo <xref:Microsoft.Office.Tools.Excel.Controls.Button> per la cella attualmente selezionata.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  In **Esplora**, selezionare Ribbon1.cs o Ribbon1. vb.  
  
4.  Nel **vista** menu, fare clic su **progettazione**.  
  
5.  Nella finestra di progettazione della barra multifunzione, fare doppio clic su **NamedRange**.  
  
6.  Sostituire il gestore eventi `NamedRange_Click` con il codice seguente.  
  
     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi definisce un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> per la cella o le celle attualmente selezionate.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  Nella finestra di progettazione della barra multifunzione, fare doppio clic su **ListObject**.  
  
8.  Sostituire il gestore eventi `ListObject_Click` con il codice seguente.  
  
     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi definisce un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> per la cella o le celle attualmente selezionate.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="removing-controls-from-the-worksheet"></a>Rimozione di controlli dal foglio di lavoro  
 I controlli non sono resi permanenti quando il foglio di lavoro viene salvato e chiuso. È necessario rimuovere a livello di codice tutti i controlli Windows Form generati prima che il foglio di lavoro venga salvato, altrimenti quando la cartella di lavoro viene nuovamente aperta, verrà visualizzata solo una struttura del controllo. Aggiungere all'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> il codice per rimuovere i controlli Windows Form dalla raccolta di controlli dell'elemento host generato. Per altre informazioni, vedere [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### <a name="to-remove-controls-from-the-worksheet"></a>Per rimuovere i controlli dal foglio di lavoro  
  
1.  In **Esplora**, selezionare ThisAddIn.cs o ThisAddIn. vb.  
  
2.  Nel **vista** menu, fare clic su **codice**.  
  
3.  Aggiungere il metodo seguente alla classe ThisAddIn. In questo codice si ottiene il primo foglio di lavoro della cartella di lavoro e viene usato il metodo `HasVstoObject` per controllare se il foglio di lavoro dispone di un oggetto foglio di lavoro generato. Se l'oggetto foglio di lavoro generato dispone di controlli, il codice ottiene tale oggetto ed esegue l'iterazione della raccolta di controlli rimuovendo questi ultimi.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  In C# è necessario creare un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Questo codice può essere inserito nel metodo `ThisAddIn_Startup`. Per ulteriori informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Sostituire il metodo `ThisAddIn_Startup` con il codice seguente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="testing-the-solution"></a>Test della soluzione  
 Aggiungere controlli a un foglio di lavoro selezionandoli da una scheda personalizzata sulla barra multifunzione. Quando si salva il foglio di lavoro, questi controlli vengono rimossi.  
  
#### <a name="to-test-the-solution"></a>Per testare la soluzione.  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare una qualsiasi cella di Sheet1.  
  
3.  Fare clic sulla scheda **Componenti aggiuntivi** .  
  
4.  Nel **group1** gruppo, fare clic su **pulsante**.  
  
     Nella cella selezionata viene visualizzato un pulsante.  
  
5.  Selezionare una cella diversa di Sheet1.  
  
6.  Nel **group1** gruppo, fare clic su **NamedRange**.  
  
     Per la cella selezionata viene definito un intervallo denominato.  
  
7.  Selezionare una serie di celle di Sheet1.  
  
8.  Nel **group1** gruppo, fare clic su **ListObject**.  
  
     Per le celle selezionate viene aggiunto un oggetto elenco.  
  
9. Salvare il foglio di lavoro.  
  
     I controlli aggiunti a Sheet1 non vengono più visualizzati.  
  
## <a name="next-steps"></a>Passaggi successivi  
 In questo argomento vengono fornite altre informazioni sui controlli nei progetti di componenti aggiuntivi VSTO per Excel:  
  
-   Per ulteriori informazioni sul salvataggio dei controlli in un foglio di lavoro, vedere l'esempio relativo ai controlli dinamici aggiuntivo di VSTO di Excel in [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Excel](../vsto/excel-solutions.md)   
 [Controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Controllo ListObject](../vsto/listobject-control.md)  
  
  