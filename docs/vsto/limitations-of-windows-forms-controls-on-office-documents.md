---
title: Limitazioni di Windows Form controlli nei documenti di Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3180de49b1ede89e6eb5e66d786247ce2700888
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitazioni dei controlli Windows Form nei documenti di Office
  Esistono alcune differenze tra i controlli Windows Form che vengono aggiunti ai documenti di Microsoft Office Word o fogli di lavoro di Microsoft Office Excel e controlli Windows Form che vengono aggiunti a un Windows Form. Ad esempio, quando si aggiunge un <xref:Microsoft.Office.Tools.Word.Controls.Button> controllo a un documento, proprietà, ad esempio <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>, e <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> non funzionano come previsto.  
  
 Molte di queste differenze sono causate dalla modalità che sono contenuti i controlli di Windows Form nei documenti. Quando un controllo Windows Form viene aggiunto a un documento, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpora un controllo ActiveX che quindi il controllo Windows Form nel documento. Il controllo Windows Form non è incorporato direttamente nel documento.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitazioni di metodi e proprietà dei controlli Windows Form  
 Sono disponibili numerosi metodi e proprietà dei controlli Windows Form che non funzionano allo stesso modo in un documento come se fossero in un Windows Form e, pertanto, si consiglia di non essere utilizzati. Ad esempio, impostando le proprietà, ad esempio `Dock` e `Anchor` interessa solo la posizione del controllo rispetto al controllo contenitore ActiveX invece che il documento. Di seguito è riportato un elenco di metodi non supportati e le proprietà dei controlli Windows Form per Word ed Excel:  
  
-   Metodi non supportati e le proprietà dei controlli di Excel:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Metodi non supportati e le proprietà dei controlli di Word:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Inoltre, non è possibile impostare il `Left` o `Top` proprietà dei controlli Windows Form che sono in linea con testo in un documento di Word. Controlli Windows Form vengono aggiunti in linea con il testo nei casi seguenti:  
  
-   A livello di codice aggiungere un controllo a un documento di Word e utilizzare un metodo che specifica un intervallo per il percorso.  
  
-   Aggiungere un controllo Windows Form a un documento di Word in fase di progettazione. È possibile modificare questo modificando il controllo nella finestra di progettazione.  
  
## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Differenze nei controlli Windows Form nei documenti di Office  
 Controlli Windows Form in genere hanno lo stesso comportamento su un documento di Office come avviene in un Windows Form, ma esistono alcune differenze. Nella tabella seguente vengono descritte le differenze esistenti per i controlli Windows Form nei documenti di Office.  
  
|Funzionalità|Differenza|  
|-------------------|----------------|  
|Ordine delle schede di controllo|È Impossibile scheda tramite i controlli inseriti in un foglio di lavoro di Excel o di un documento di Word.|  
|Raggruppamento di controllo|Non è possibile utilizzare un <xref:System.Windows.Forms.GroupBox> controllo per contenere altri controlli in un documento di Office. Quando si aggiungono più pulsanti di opzione direttamente al documento, i pulsanti di opzione non si escludono a vicenda. È possibile scrivere codice per rendere i pulsanti di opzione si escludono a vicenda. Tuttavia, l'approccio consigliato consiste nell'aggiungere i pulsanti di opzione in un controllo utente e quindi aggiungere il controllo utente al documento. Per ulteriori informazioni, vedere l'esempio di controlli di Word o Excel di esempio di controlli in [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).|  
|Tipo di controllo|Vengono eseguito il wrapping di controlli Windows Form nei documenti in una classe fornita dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i controlli che offre funzionalità aggiuntive specifiche per il foglio di lavoro di Excel o di un documento di Word. Ad esempio, se dispone di un `Button` di controllo in un foglio di lavoro di Excel, assicurarsi di specificare il tipo di <xref:Microsoft.Office.Tools.Excel.Controls.Button> anziché <xref:System.Windows.Forms.Button> quando si fa riferimento o il cast dell'oggetto.|  
|Posizione del controllo e le dimensioni|Le dimensioni e la posizione del controllo è determinata dalle proprietà che fanno parte del contenitore di controlli ActiveX. Le proprietà del controllo ActiveX accettano valori diversi da quelli di proprietà equivalenti di un controllo Windows Form. Quando si imposta la `Top`, `Left`, `Height`, o `Width` delle proprietà di un controllo, è misurata in punti, invece di pixel.|  
|Posizione del controllo nei documenti di Word|Se si aggiungono controlli a un layout di flusso, tenere presente che i controlli di flusso con il contenuto modificato il contenuto. Non è possibile ancorare il controllo a un paragrafo quando si trascina dal **della casella degli strumenti** perché il controllo viene aggiunto al documento di Word in linea con il testo. Se si utilizza un altro metodo per aggiungere il controllo, ad esempio fare doppio clic sul controllo, il controllo viene inserito in base all'opzione di Word che sono stati impostati per l'inserimento di immagini.<br /><br /> Non è possibile impostare il `Left` o `Top` proprietà di un controllo che è in linea con il testo.<br /><br /> È possibile inserire controlli in un'intestazione o piè di pagina o all'interno di un documento secondario.|  
|Eventi di controllo|Quando il controllo è selezionato, vengono generati eventi nell'ordine seguente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando il controllo è deselezionato, genera eventi nell'ordine seguente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Controllo ridimensionamento|Quando si modifica l'impostazione dello zoom di un documento su un valore diverso da 100%, i controlli sono disabilitati, anche se sembrano scala con il documento. Ad esempio, se si sceglie un pulsante quando il documento si trova in % 130 zoom, un messaggio indicherà che il controllo è stato disabilitato finché non lo zoom è impostato su 100%. I controlli funzionerà correttamente quando si modifica il valore di zoom su 100%.|  
|Valori delle proprietà di controllo|Anche se le proprietà dei controlli in un Windows Form sono impostate su un valore intero, vengano impostate per una singola per i controlli in un documento di Word. In Excel, sono impostati i valori delle proprietà dei controlli in un valore double. Se il `Height` e `Width` proprietà di un controllo in un foglio di lavoro superano le dimensioni del foglio di lavoro o dello schermo, il valore viene troncato.|  
|Ridimensionamento del controllo|Se si ridimensiona un controllo nel documento utilizzando uno dei quadratini di otto ridimensionamento, le nuove dimensioni del controllo non vengono riflesse nel **proprietà** finestra fino a quando non si seleziona di nuovo il controllo.|  
|Controllare il comportamento|Controlli in un foglio di lavoro di Excel potrebbero funzionare in modo imprevedibile quando il foglio di lavoro è divisa. Ad esempio, l'accesso a un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> nel foglio di lavoro potrebbe essere disponibile solo in una delle finestre.|  
|Denominazione di controllo|È possibile utilizzare parole riservate per i nomi dei controlli. Ad esempio, se si aggiunge un <xref:Microsoft.Office.Tools.Excel.Controls.Button> a un foglio di lavoro e modificare il nome in **sistema**, si verificano errori quando si compila il progetto.|  
|Aggiunta di controlli a livello di codice|Non utilizzare il costruttore del controllo per aggiungere un controllo al documento in fase di esecuzione. Utilizzare invece i metodi di supporto forniti dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ad esempio, utilizzare il <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> per aggiungere un pulsante in un foglio di lavoro. Se si desidera aggiungere un controllo che non è supportato da questi metodi di supporto, è possibile utilizzare il metodo AddControl. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Copia di controlli|Se si copia un controllo Windows Form e incollarlo in un documento in fase di esecuzione, un contenitore vuoto controllo ActiveX viene incollato nel documento. Il controllo Windows Form non viene visualizzato nella nuova posizione e code-behind del controllo originale non viene copiato al contenitore del controllo ActiveX.|  
  
## <a name="limitations-in-document-level-projects"></a>Limitazioni nei progetti a livello di documento  
 Alcune limitazioni dell'utilizzo di controlli Windows Form nei documenti sono univoche per i progetti a livello di documento.  
  
### <a name="control-support-at-design-time"></a>Supporto per il controllo in fase di progettazione  
 Determinati controlli Windows Form vengono rimosse le **della casella degli strumenti** quando un foglio di lavoro di Excel o di un documento di Word è aperto nella finestra di progettazione di Visual Studio. Ciò è dovuto a problemi tecnici o perché la funzionalità è già disponibile in Word o Excel. I progetti di Excel e Word supportano tutti i controlli Windows Form e altri componenti che vengono visualizzati di **della casella degli strumenti** quando il documento ha lo stato attivo ed è anche possibile aggiungere controlli di terze parti a un documento o foglio di lavoro.  
  
> [!NOTE]  
>  Tutti i controlli vengono rimossi dal **della casella degli strumenti** quando un documento è protetto. Per informazioni sulla protezione dei documenti, vedere [protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  I controlli di terze parti devono avere la <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo impostato su **true** per poter essere usato in una soluzione Office.  
  
 Controlli e i componenti seguenti non sono disponibili nel **della casella degli strumenti**:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### <a name="support-for-legacy-activex-controls"></a>Supporto per i controlli ActiveX Legacy  
 Se si crea un progetto di Office a livello di documento che utilizza un documento di Word o una cartella di lavoro di Excel che contiene controlli ActiveX, la funzionalità dei controlli ActiveX non andrà persa. Tuttavia, non vi è alcun supporto per l'aggiunta di nuovi controlli ActiveX ai documenti all'interno di Visual Studio. Ad esempio, se il documento di Word è un pulsante di **controllo** della casella degli strumenti che esegue un esempio di Visual Basic, Applications Edition (VBA), continuerà a eseguire la macro dopo che il documento è stato utilizzato in un progetto di Office. Tuttavia, è consigliabile rimuovere i controlli ActiveX e le macro VBA e sostituirli con controlli Windows Form e codice gestito.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: Aggiungere controlli Windows Forms a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  