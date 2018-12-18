---
title: 'Procedura: aggiungere controlli contenuto ai documenti di Word | Documenti Microsoft'
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
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b1dd59fc777c012f92baaf96302f7cf031ad151c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Procedura: aggiungere controlli del contenuto ai documenti di Word
  Nei progetti di Word a livello di documento è possibile aggiungere controlli contenuto al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO di Word è possibile aggiungere controlli contenuto a qualsiasi documento aperto in fase di esecuzione.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli contenuto in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli contenuto in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli contenuto in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per informazioni sui controlli contenuto, vedere [Content Controls](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Adding Content Controls at Design Time  
 Sono disponibili varie modalità di aggiunta di controlli contenuto al documento in un progetto a livello di documento in fase di progettazione:  
  
-   Aggiungere un controllo contenuto dalla scheda **Controlli Word** della **Casella degli strumenti**.  
  
-   Aggiungere un controllo contenuto al documento nello stesso modo in cui si aggiunge un controllo contenuto nativo in Word.  
  
-   Trascinare un controllo contenuto nel documento dalla finestra **Origini dati** . Questa modalità è utile quando si vuole associare il controllo ai dati al momento della creazione del controllo. Per ulteriori informazioni, vedere [procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md) e [procedura: popolare documenti con dati da un Database](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Per aggiungere un controllo contenuto a un documento tramite la casella degli strumenti  
  
1.  Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il controllo contenuto o selezionare il testo che deve essere sostituito dal controllo contenuto.  
  
2.  Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Word** .  
  
3.  Aggiungere il controllo in uno dei modi seguenti:  
  
    -   Fare doppio clic su un controllo contenuto nella **Casella degli strumenti**.  
  
         oppure  
  
    -   Fare clic su un controllo contenuto nella **Casella degli strumenti** e quindi premere INVIO.  
  
         oppure  
  
    -   Trascinare un controllo contenuto dalla **Casella degli strumenti** nel documento. Il controllo contenuto viene aggiunto in corrispondenza della selezione corrente nel documento, non in corrispondenza della posizione del puntatore del mouse.  
  
> [!NOTE]  
>  Non è possibile aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> usando la **Casella degli strumenti**. È possibile aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> solo in Word o in fase di esecuzione.  
  
> [!NOTE]  
>  Visual Studio non fornisce un controllo contenuto casella di controllo nella casella degli strumenti. Per aggiungere un controllo contenuto casella di controllo al documento, è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> a livello di codice. Per altre informazioni, vedere [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Per aggiungere un controllo contenuto a un documento in Word  
  
1.  Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il controllo contenuto o selezionare il testo che deve essere sostituito dal controllo contenuto.  
  
2.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  Nel gruppo **Controlli** fare clic sull'icona del controllo contenuto che si desidera aggiungere.  
  
##  <a name="runtimedoclevel"></a> Adding Content Controls at Run Time in a Document-Level Project  
 È possibile aggiungere controlli contenuto a livello di codice al documento in fase di esecuzione usando i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> della classe `ThisDocument` nel progetto. Ogni metodo ha tre overload che è possibile usare per aggiungere un controllo contenuto nei modi seguenti:  
  
-   Aggiungere un controllo in corrispondenza della selezione corrente.  
  
-   Aggiungere un controllo in corrispondenza di un intervallo specificato.  
  
-   Aggiungere un controllo basato su un controllo contenuto nativo nel documento.  
  
 I controlli contenuto creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un controllo contenuto nativo rimane nel documento. È possibile ricreare un controllo contenuto basato su un controllo contenuto nativo alla successiva apertura del documento. Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Per aggiungere un controllo contenuto casella di controllo a un documento in un progetto di Word 2010, è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> . Per altre informazioni, vedere [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-at-the-current-selection"></a>Per aggiungere un controllo contenuto in corrispondenza della selezione corrente  
  
1.  Utilizzare un <xref:Microsoft.Office.Tools.Word.ControlCollection> metodo che presenta il nome `Add` \< *classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), e che dispone di un singolo parametro per il nome del nuovo controllo.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddRichTextControlAtSelection` dal gestore eventi `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
#### <a name="to-add-a-content-control-at-a-specified-range"></a>Per aggiungere un controllo contenuto in corrispondenza di un intervallo specificato  
  
1.  Utilizzare un <xref:Microsoft.Office.Tools.Word.ControlCollection> metodo che presenta il nome `Add` \< *classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), e che ha un <xref:Microsoft.Office.Interop.Word.Range> parametro.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddRichTextControlAtRange` dal gestore eventi `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Per aggiungere un controllo contenuto basato su un controllo contenuto nativo  
  
1.  Utilizzare un <xref:Microsoft.Office.Tools.Word.ControlCollection> metodo che presenta il nome `Add` \< *classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), e che presenta un parametro Microsoft.Office.Interop.Word.ContentControl.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per creare un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> per ogni controllo in formato RTF nativo nel documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `CreateRichTextControlsFromNativeControls` dal gestore eventi `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli contenuto in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere controlli contenuto a livello di codice a qualsiasi documento aperto in fase di esecuzione usando un componente aggiuntivo VSTO. A tale scopo, generare un elemento host <xref:Microsoft.Office.Tools.Word.Document> basato su un documento aperto e quindi usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> di tale elemento host. Ogni metodo ha tre overload che è possibile usare per aggiungere un controllo contenuto nei modi seguenti:  
  
-   Aggiungere un controllo in corrispondenza della selezione corrente.  
  
-   Aggiungere un controllo in corrispondenza di un intervallo specificato.  
  
-   Aggiungere un controllo basato su un controllo contenuto nativo nel documento.  
  
 I controlli contenuto creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un controllo contenuto nativo rimane nel documento. È possibile ricreare un controllo contenuto basato su un controllo contenuto nativo alla successiva apertura del documento. Per altre informazioni, vedere [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Per ulteriori informazioni sulla generazione di elementi host nei progetti di componente aggiuntivo VSTO, vedere [estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Per aggiungere un controllo contenuto casella di controllo a un documento è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> . Per altre informazioni, vedere [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-at-the-current-selection"></a>Per aggiungere un controllo contenuto in corrispondenza della selezione corrente  
  
1.  Utilizzare un <xref:Microsoft.Office.Tools.Word.ControlCollection> metodo che presenta il nome `Add` \< *classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), e che dispone di un singolo parametro per il nome del nuovo controllo.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento attivo. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddRichTextControlAtSelection` dal gestore eventi `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
#### <a name="to-add-a-content-control-at-a-specified-range"></a>Per aggiungere un controllo contenuto in corrispondenza di un intervallo specificato  
  
1.  Utilizzare un <xref:Microsoft.Office.Tools.Word.ControlCollection> metodo che presenta il nome `Add` \< *classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), e che ha un <xref:Microsoft.Office.Interop.Word.Range> parametro.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento attivo. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddRichTextControlAtRange` dal gestore eventi `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Per aggiungere un controllo contenuto basato su un controllo contenuto nativo  
  
1.  Utilizzare un <xref:Microsoft.Office.Tools.Word.ControlCollection> metodo che presenta il nome `Add` \< *classe del controllo*> (dove *classe del controllo* è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), e che presenta un parametro Microsoft.Office.Interop.Word.ContentControl.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per creare un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> per ogni controllo in formato RTF nativo in un documento, dopo l'apertura del documento. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     Per C#, è anche necessario collegare il gestore eventi `Application_DocumentOpen` all'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  