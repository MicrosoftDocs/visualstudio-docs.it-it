---
title: 'Procedura: aggiungere controlli Windows Form a documenti di Office | Documenti Microsoft'
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 937c64f8fadf8763d4e5b3ad32489262cddafdfd
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Procedura: aggiungere controlli Windows Form a documenti di Office
  È possibile aggiungere controlli Windows Form a documenti di Microsoft Office Excel e Microsoft Office Word in fase di progettazione in progetti a livello di documento. È possibile aggiungere controlli nelle personalizzazioni a livello di documento e nei componenti aggiuntivi VSTO in fase di esecuzione. È possibile, ad esempio, aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> al foglio di lavoro in modo che l'utente possa effettuare una selezione da un elenco di opzioni.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli in fase di esecuzione nei progetti a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli in fase di esecuzione in componenti aggiuntivi VSTO](#runtimeaddin)  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [procedura ricerca per categorie: aggiungere controlli all'area di un documento in fase di esecuzione?](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a>Aggiunta di controlli in fase di progettazione  
 Sono disponibili varie modalità di aggiunta di controlli Windows Form al documento in un progetto a livello di documento in fase di progettazione.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Per trascinare un controllo Windows sul documento  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nel **controlli comuni** scheda della finestra di **della casella degli strumenti**, fare clic sul controllo a cui si desidera aggiungere e trascinarlo nel documento.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.  
  
#### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Per trascinare un controllo Windows Form sul documento  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nel **controlli comuni** scheda della finestra di **della casella degli strumenti**, fare clic sul controllo a cui si desidera aggiungere.  
  
3.  Nel documento fare clic sul punto in cui si vuole posizionare l'angolo superiore sinistro del controllo e trascinare fino al punto in cui si vuole posizionare l'angolo inferiore destro.  
  
     Il controllo viene aggiunto al documento con la dimensione e la posizione specificate.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, si noterà **=EMBED("WinForms.Control.Host","")** nel **barra della Formula**. Questo testo è necessario e non deve essere eliminato.  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Per aggiungere un controllo Windows al documento facendo un singolo clic sul controllo  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nel **controlli comuni** scheda della finestra di **della casella degli strumenti**, fare clic sul controllo a cui si desidera aggiungere  
  
3.  Nel documento fare clic nel punto in cui si vuole aggiungere il controllo.  
  
     Il controllo viene aggiunto al documento con la dimensione predefinita.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Per aggiungere un controllo Windows al documento facendo un doppio clic sul controllo  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nel **controlli comuni** scheda della finestra il **della casella degli strumenti**, fare doppio clic sul controllo da aggiungere.  
  
     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Per aggiungere un controllo Windows Form al documento premendo INVIO  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nel **controlli comuni** scheda della finestra di **della casella degli strumenti**, fare clic sul controllo a cui si desidera aggiungere e premere INVIO.  
  
     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.  
  
##  <a name="runtimedoclevel"></a>Aggiunta di controlli in fase di esecuzione nei progetti a livello di documento  
 È possibile aggiungere controlli Windows Form a livello di codice a un documento in fase di esecuzione. In Word usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> della classe `ThisDocument`. In Excel, usare i metodi del <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> proprietà di un `Sheet`  *n*  classe. Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.  
  
 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso. È possibile ricreare il controllo alla prossima apertura del documento. Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-windows-forms-control-at-run-time"></a>Per aggiungere un controllo Windows Form in fase di esecuzione  
  
1.  Utilizzare un metodo che presenta il nome del componente\<*classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo Windows Form che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     Esempio di codice seguente viene illustrato come aggiungere un <xref:Microsoft.Office.Tools.Excel.Controls.Button> alla cella **C5** di `Sheet1` in un progetto a livello di documento per Excel.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a>Aggiunta di controlli in fase di esecuzione nei componenti aggiuntivi VSTO  
 È possibile aggiungere controlli Windows Form a livello di codice a qualsiasi documento aperto in fase di esecuzione. Generare innanzitutto un elemento host basato su un foglio di lavoro o un documento aperto. In Word usare quindi i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> del nuovo elemento host. In Excel usare i metodi della proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> del nuovo elemento host. Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.  
  
 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso. È possibile ricreare il controllo alla prossima apertura del documento. Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Per ulteriori informazioni sulla generazione di elementi host nei progetti di componente aggiuntivo VSTO, vedere [estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-windows-forms-control-at-run-time"></a>Per aggiungere un controllo Windows Form in fase di esecuzione  
  
1.  Utilizzare un metodo che presenta il nome del componente\<*classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo Windows Form che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  Progetti di componente aggiuntivo VSTO di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario aggiungere un riferimento all'assembly Microsoft.Office.Tools.Excel.v4.0.Utilities.dll o Microsoft.Office.Tools.Word.v4.0.Utilities.dll prima di poter accedere Aggiungi\< *classe del controllo*> metodi.  
  
     L'esempio di codice seguente illustra come aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> al primo paragrafo del documento attivo mediante un componente aggiuntivo VSTO per Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: ridimensionare i controlli all'interno delle celle del foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  