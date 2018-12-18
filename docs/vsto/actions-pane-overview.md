---
title: Panoramica del riquadro azioni | Documenti Microsoft
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
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0e3fb356c00b3e9943ba8aff696283d4c5339e18
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="actions-pane-overview"></a>Cenni preliminari sul riquadro delle azioni
  Un riquadro azioni è personalizzabile **azioni documenti** riquadro attività associato a un documento di Microsoft Office Word specifico o una cartella di lavoro di Microsoft Office Excel. È ospitato all'interno del riquadro attività di Office insieme ad altri riquadri attività predefiniti come il **origine XML** riquadro in Excel o **stili e formattazione** riquadro attività in Word. È possibile usare controlli Windows Form o controlli WPF per progettare l'interfaccia utente del riquadro azioni.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È possibile creare un riquadro azioni solo in una personalizzazione a livello di documento per Word o Excel. Non è possibile cerare un riquadro azioni in un componente aggiuntivo VSTO. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Il riquadro azioni è diverso dai riquadri attività. I riquadri attività personalizzati sono associati all'applicazione e non a un documento specifico. È possibile creare riquadri attività personalizzati in componenti aggiuntivi VSTO per alcune applicazioni di Microsoft Office. Per ulteriori informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [come si ricerca per categorie: utilizzare WPF controlli all'interno di un riquadro azioni di Excel?](http://go.microsoft.com/fwlink/?LinkId=132763).  
  
## <a name="displaying-the-actions-pane"></a>Visualizzazione del riquadro azioni  
 Il riquadro azioni è rappresentato dalla classe <xref:Microsoft.Office.Tools.ActionsPane>. Quando si crea un progetto a livello di documento, un'istanza di questa classe è disponibile per il codice usando il campo `ActionsPane` della classe `ThisWorkbook` (per Excel) o `ThisDocument` (per Word) nel progetto. Per visualizzare il riquadro azioni, aggiungere un controllo Windows Form alla proprietà <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> del campo `ActionsPane`. L'esempio di codice seguente aggiunge un controllo denominato `actions` al riquadro azioni.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
 Il riquadro azioni diventa visibile in fase di esecuzione non appena vi si aggiunge in modo esplicito un controllo. Dopo che il riquadro azioni viene visualizzato, è possibile aggiungere o rimuovere dinamicamente controlli in risposta alle azioni dell'utente. In genere, è necessario aggiungere il codice per visualizzare il riquadro azioni nel gestore eventi `Startup` di `ThisDocument` o `ThisWorkbook` in modo che il riquadro azioni sia visibile quando l'utente apre per la prima volta il documento. Potrebbe tuttavia essere necessario visualizzare il riquadro azioni solo in risposta all'azione di un utente nel documento. Ad esempio, è possibile aggiungere il codice all'evento `Click` di un controllo nel documento.  
  
### <a name="adding-multiple-controls-to-the-actions-pane"></a>Aggiunta di più controlli al riquadro azioni  
 Se si aggiungono più controlli al riquadro azioni, nella maggior parte dei casi è consigliabile raggruppare i controlli in un controllo utente e quindi aggiungere il controllo utente alla proprietà <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>. Questo processo include i due passaggi seguenti:  
  
1.  Creare l'interfaccia utente (UI) del riquadro azioni aggiungendo un **controllo riquadro azioni** o **controllo utente** elemento al progetto. Entrambi questi elementi includono una classe <xref:System.Windows.Forms.UserControl> personalizzata di Windows Form. Il **controllo riquadro azioni** e **controllo utente** gli elementi sono equivalenti; l'unica differenza è il relativo nome.  
  
2.  Aggiungere controlli Windows Form a <xref:System.Windows.Forms.UserControl> usando la finestra di progettazione o scrivendo codice.  
  
    > [!NOTE]  
    >  È anche possibile aggiungere controlli WPF al riquadro azioni aggiungendo un oggetto <xref:System.Windows.Controls.UserControl> all'oggetto <xref:System.Windows.Forms.UserControl> di Windows Form. Per ulteriori informazioni, vedere [utilizzo dei controlli WPF nelle soluzioni Office](../vsto/using-wpf-controls-in-office-solutions.md).  
  
3.  Aggiungere un'istanza del controllo utente personalizzato ai controlli contenuti nel campo `ActionsPane` della classe `ThisWorkbook` (per Excel) o `ThisDocument` (per Word) nel progetto.  
  
 Per esempi che illustrano il processo in modo più dettagliato, vedere [procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
## <a name="hiding-the-actions-pane"></a>Nascondere il riquadro azioni  
 Benché la classe <xref:Microsoft.Office.Tools.ActionsPane> includa un metodo <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> e una proprietà <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, non è possibile rimuovere il riquadro azioni dall'interfaccia utente usando membri della classe <xref:Microsoft.Office.Tools.ActionsPane> stessa. La chiamata il <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metodo o l'impostazione di <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> proprietà **false** nasconde solo i controlli nel riquadro azioni, non nasconde il riquadro attività.  
  
 Per nascondere il riquadro attività nella soluzione, sono disponibili diverse opzioni:  
  
-   Per Word, impostare il <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> proprietà del <xref:Microsoft.Office.Interop.Word.TaskPane> oggetto che rappresenta il riquadro attività Azioni documenti su **false**. L'esempio di codice seguente deve essere eseguito dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  
  
-   In Excel, impostare il <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> proprietà del <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> oggetto **false**. L'esempio di codice seguente deve essere eseguito dalla classe `ThisWorkbook` nel progetto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  
  
-   Per Word o Excel, in alternativa è possibile impostare il <xref:Microsoft.Office.Core.CommandBar.Visible%2A> proprietà della barra dei comandi che rappresenta il riquadro attività su **false**. L'esempio di codice seguente deve essere eseguito dalla classe `ThisDocument` o `ThisWorkbook` nel progetto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  
  
### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>Cancellazione del riquadro azioni all'apertura del documento  
 Se l'utente salva il documento mentre il riquadro azioni è visibile, questo è visibile ogni volta che il documento viene aperto, sia che contenga o meno controlli. Per controllare i momenti in cui viene visualizzato, chiamare il metodo <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> del campo `ActionsPane` nel gestore eventi `Startup` di `ThisDocument` o `ThisWorkbook` per fare in modo che il riquadro azioni non sia visibile all'apertura del documento.  
  
### <a name="determining-when-the-actions-pane-is-closed"></a>Scelta dei momenti in cui il riquadro azioni viene chiuso  
 Quando il riquadro azioni viene chiuso, non viene generato alcun evento. Benché la classe <xref:Microsoft.Office.Tools.ActionsPane> includa un evento <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, questo evento non viene generato quando l'utente finale chiude il riquadro azioni. Al contrario, questo evento viene generato quando i controlli nel riquadro azioni vengono nascosti chiamando il <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> (metodo) o impostando la <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> proprietà **false**.  
  
 Se l'utente finale chiude il riquadro azioni, può visualizzarlo di nuovo eseguendo una delle procedure seguenti nell'interfaccia utente (UI) dell'applicazione.  
  
##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Per visualizzare il riquadro azioni usando l'interfaccia utente di Word o Excel  
  
1.  Sulla barra multifunzione, fare clic su di **vista** scheda.  
  
2.  Nel **Mostra/Nascondi** gruppo, fare clic su di **azioni documenti** interruttore.  
  
## <a name="programming-actions-pane-events"></a>Programmazione di eventi del riquadro attività  
 È possibile aggiungere più controlli utente al riquadro azioni e quindi scrivere codice in risposta a eventi nel documento mostrando e nascondendo i controlli utente. Se si esegue il mapping di elementi XML Schema al documento, è possibile mostrare determinati controlli utente nel riquadro azioni ogni volta che il punto di inserimento si trova all'interno di uno degli elementi XML. Per ulteriori informazioni, vedere [come: mappa di schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) e [come: mappa di schemi a fogli di lavoro all'interno di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  
  
 È anche possibile scrivere codice per rispondere agli eventi di qualsiasi oggetto, tra cui controlli host, applicazioni o eventi del documento. Per ulteriori informazioni vedere [procedura dettagliata: programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
## <a name="binding-data-to-controls-on-the-actions-pane"></a>Associazione di dati a controlli nel riquadro azioni  
 I controlli nel riquadro azioni hanno le stesse caratteristiche di data binding di quelli in Windows Form. È possibile associare i controlli a origini dati come set di dati, set di dati tipizzati e XML. Per altre informazioni, vedere [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 È possibile associare controlli nel riquadro azioni e controlli nel documento allo stesso set di dati. Ad esempio, è possibile creare una relazione master/dettaglio tra i controlli nel riquadro azioni e i controlli nel foglio di lavoro. Per ulteriori informazioni, vedere [procedura dettagliata: associazione di dati a controlli in un riquadro azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
## <a name="validating-data-in-actions-pane-controls"></a>Convalida di dati in controlli del riquadro azioni  
 Se si visualizza una finestra di messaggio nel gestore eventi <xref:System.Windows.Forms.Control.Validating> di un controllo nel riquadro azioni, l'evento potrebbe essere generato una seconda volta quando lo stato attivo passa dal controllo alla finestra di messaggio. Per evitare questo problema, usare un controllo <xref:System.Windows.Forms.ErrorProvider> per visualizzare eventuali messaggi di errore di convalida.  
  
## <a name="user-control-stacking-order"></a>Ordine di sovrapposizione dei controlli utente  
 Se si usano più controlli utente, è possibile scrivere codice per sovrapporre correttamente i controlli utenti nel riquadro azioni, quando è ancorato in verticale o in orizzontale. È possibile impostare l'ordine di sovrapposizione nel riquadro azioni usando l'enumerazione <xref:Microsoft.Office.Tools.StackStyle> della proprietà <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Per ulteriori informazioni, vedere [procedura: gestire il Layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)  
  
 La proprietà <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> può accettare i valori dell'enumerazione <xref:Microsoft.Office.Tools.StackStyle> seguenti.  
  
|Stile di sovrapposizione|Definizione|  
|--------------------|----------------|  
|FromBottom|Sovrapposizione dal basso del riquadro azioni.|  
|FromLeft|Sovrapposizione dal lato sinistro del riquadro azioni.|  
|FromRight|Sovrapposizione dal lato destro del riquadro azioni.|  
|FromTop|Sovrapposizione dall'alto del riquadro azioni.|  
|nessuno|Nessun ordine di sovrapposizione definito. L'ordine è controllato dallo sviluppatore.|  
  
 Il codice seguente imposta la proprietà <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> per ordinare i controlli utente dall'alto del riquadro azioni.  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  
  
## <a name="anchoring-controls"></a>Ancoraggio dei controlli  
 Se l'utente ridimensiona il riquadro azioni in fase di esecuzione, i controlli possono essere ridimensionati insieme al riquadro azioni. È possibile usare la proprietà <xref:System.Windows.Forms.Control.Anchor%2A> di un controllo Windows Form per ancorare i controlli al riquadro azioni. È anche possibile ancorare i controlli Windows Form nel controllo utente allo stesso modo. Per ulteriori informazioni, vedere [procedura: ancorare i controlli in Windows Form](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
## <a name="resizing-the-actions-pane"></a>Ridimensionamento del riquadro azioni  
 Non è possibile modificare direttamente le dimensioni di un oggetto <xref:Microsoft.Office.Tools.ActionsPane> perché <xref:Microsoft.Office.Tools.ActionsPane> è incorporato nel riquadro attività. È tuttavia modificare a livello di codice la larghezza del riquadro attività impostando la proprietà <xref:Microsoft.Office.Core.CommandBar.Width%2A> dell'oggetto <xref:Microsoft.Office.Core.CommandBar> che rappresenta il riquadro attività. È possibile modificare l'altezza del riquadro attività se è ancorato in orizzontale o se è mobile.  
  
 Il ridimensionamento del riquadro attività a livello di codice è in genere sconsigliato, perché l'utente dovrebbe poter selezionare le dimensioni del riquadro attività più adatte alle sue esigenze. Tuttavia, se è necessario ridimensionare la larghezza del riquadro attività, è possibile usare il codice seguente a questo scopo.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  
  
## <a name="repositioning-the-actions-pane"></a>Riposizionamento del riquadro azioni  
 Non è possibile riposizionare direttamente l'oggetto <xref:Microsoft.Office.Tools.ActionsPane> perché è incorporato nel riquadro attività. È tuttavia possibile spostare il riquadro attività a livello di codice impostando la proprietà <xref:Microsoft.Office.Core.CommandBar.Position%2A> dell'oggetto <xref:Microsoft.Office.Core.CommandBar> che rappresenta il riquadro attività.  
  
 Il riposizionamento del riquadro attività a livello di codice è in genere sconsigliato, perché l'utente dovrebbe poter scegliere la posizione del riquadro attività più adatta alle sue esigenze. Tuttavia, se è necessario spostare il riquadro attività in una posizione specifica, è possibile usare il codice seguente a questo scopo.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  Gli utenti finali possono riposizionare manualmente il riquadro attività in qualsiasi momento. Non esiste alcun modo per garantire che il riquadro attività resti ancorato nella posizione indicata a livello di codice. Tuttavia, è possibile controllare le modifiche di orientamento e garantire che i controlli nel riquadro azioni siano sovrapposti nella direzione corretta. Per ulteriori informazioni, vedere [procedura: gestire il Layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 L'impostazione delle proprietà <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> e <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> di <xref:Microsoft.Office.Tools.ActionsPane> non comporta la modifica della posizione, perché l'oggetto <xref:Microsoft.Office.Tools.ActionsPane> è incorporato nel riquadro attività.  
  
 Se il riquadro attività non è ancorato, è possibile impostare le proprietà <xref:Microsoft.Office.Core.CommandBar.Top%2A> e <xref:Microsoft.Office.Core.CommandBar.Left%2A> dell'oggetto <xref:Microsoft.Office.Core.CommandBar> che rappresenta il riquadro attività. Il codice seguente sposta un riquadro attività non ancorato nell'angolo superiore sinistro del documento.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di controlli WPF nelle soluzioni Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura dettagliata: Inserimento di testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procedura dettagliata: Associazione dati a controlli in un riquadro delle azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Procedura dettagliata: Associazione dati a controlli in un riquadro azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Procedura: gestire il Layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procedura dettagliata: inserimento di testo in un documento da un riquadro Azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  