---
title: 'Procedura: Aggiungere controlli segnalibro ai documenti di Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e58525d20efe17d24cd916b5e9eff79c7da59d7
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647790"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Procedura: Aggiungere controlli segnalibro ai documenti di Word
  Nei progetti a livello di documento, è possibile aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark> controlli al documento nel progetto in fase di progettazione o in fase di esecuzione. Nei progetti di componente aggiuntivo VSTO, è possibile aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark> controlli a qualsiasi documento aperto in fase di esecuzione.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
- [Aggiungere i controlli Bookmark in fase di progettazione](#designtime)  
  
- [Aggiungere i controlli Bookmark in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
- [Aggiungere i controlli Bookmark in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
  Per altre informazioni sulle <xref:Microsoft.Office.Tools.Word.Bookmark> controlli, vedere [Bookmark (controllo)](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Aggiungere i controlli Bookmark in fase di progettazione  
 Sono disponibili varie modalità di aggiunta di controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento in un progetto a livello di documento in fase di progettazione:  
  
- Dalla **Casella degli strumenti**di Visual Studio.  
  
   È possibile trascinare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> dalla **Casella degli strumenti** al documento. Scegliere questa modalità se si sta già usando la **Casella degli strumenti** per aggiungere controlli Windows Form al documento.  
  
- Da Word.  
  
   È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> al documento nello stesso modo in cui si aggiunge un segnalibro nativo. Il vantaggio di questa modalità è la possibilità di assegnare un nome al controllo al momento della creazione.  
  
- Dalla finestra **Origini dati** .  
  
   È possibile trascinare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento dalla finestra **Origini dati** . Questa modalità è utile quando si vuole contemporaneamente associare il controllo ai dati. È possibile aggiungere il controllo host nello stesso modo in cui si aggiunge un controllo Windows Form dalla finestra **Origini dati** . Per altre informazioni, vedere [Data binding e Windows Form](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Per aggiungere un controllo Bookmark a un documento dalla casella degli strumenti  
  
1.  Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Word** .  
  
2.  Trascinare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo Bookmark** .  
  
3.  Selezionare il testo o altri elementi che si desidera includere nel segnalibro.  
  
4.  Fare clic su **OK**.  
  
     Se non si vuole mantenere il nome del segnalibro predefinito, è possibile modificarlo nella finestra **Proprietà** .  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Per aggiungere un controllo Bookmark a un documento in Word  
  
1.  Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il segnalibro o selezionare il testo che deve essere racchiuso nel segnalibro.  
  
2.  Nella scheda **Inserisci** della barra multifunzione fare clic sul pulsante **Segnalibro** nel gruppo **Collegamenti** .  
  
3.  Nella finestra di dialogo **Segnalibro** digitare il nome del nuovo segnalibro e fare clic su **Aggiungi**.  
  
##  <a name="runtimedoclevel"></a> Aggiungere i controlli Bookmark in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark> consente di controllare a livello di codice al documento in fase di esecuzione usando metodi del <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> proprietà del `ThisDocument` classe nel progetto. Ci sono due overload di metodo che è possibile usare per aggiungere un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nei modi seguenti:  
  
- Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> in corrispondenza di un intervallo specificato.  
  
- Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo nel documento (ovvero un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo rimane nel documento. È possibile ricreare un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo alla successiva apertura del documento. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Per aggiungere un controllo Bookmark a un documento a livello di codice  
  
1.  Nel gestore eventi `ThisDocument_Startup` nel progetto inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> al primo paragrafo nel documento.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Se si vuole creare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> da un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>esistente, usare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> e passare l'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>esistente.  
  
##  <a name="runtimeaddin"></a> Aggiungere i controlli Bookmark in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark> controlli a livello di codice a qualsiasi documento aperto in fase di esecuzione usando un componente aggiuntivo VSTO. A tale scopo, generare un elemento host <xref:Microsoft.Office.Tools.Word.Document> basato su un documento aperto e quindi usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> di tale elemento host. Ci sono due overload di metodo che è possibile usare per aggiungere un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nei modi seguenti:  
  
- Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> in corrispondenza di un intervallo specificato.  
  
- Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo nel documento (ovvero un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo rimane nel documento. È possibile ricreare un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo alla successiva apertura del documento. Per altre informazioni, vedere [mantengono i controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  Per altre informazioni sulla generazione di elementi host nei progetti di componente aggiuntivo VSTO, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Per aggiungere un controllo Bookmark in corrispondenza di un intervallo specificato  
  
1.  Usare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> e passare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> dove si vuole aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     L'esempio di codice seguente aggiunge un nuovo oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> all'inizio del documento attivo. Per usare questo esempio, eseguire il codice dal gestore eventi `ThisAddIn_Startup` in un progetto di componente aggiuntivo VSTO di Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Per aggiungere un controllo Bookmark basato su un controllo Bookmark nativo  
  
1.  Usare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> e passare l'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> esistente che si vuole usare come base per il nuovo oggetto <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     L'esempio di codice seguente crea un nuovo oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato sul primo oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nel documento attivo. Per usare questo esempio, eseguire il codice dal gestore eventi `ThisAddIn_Startup` in un progetto di componente aggiuntivo VSTO di Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedura: Ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)  
  
  