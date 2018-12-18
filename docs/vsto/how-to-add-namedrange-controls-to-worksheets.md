---
title: 'Procedura: aggiungere controlli NamedRange a fogli di lavoro | Documenti Microsoft'
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
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ef0ec1846a4ef75200fa6d37f137ca1ab1d70f48
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Procedura: aggiungere controlli NamedRange a fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> in fase di esecuzione nei progetti di componente aggiuntivo VSTO.  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli NamedRange in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli NamedRange in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per altre informazioni sui controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> , vedere [NamedRange Control](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Adding NamedRange Controls at Design Time  
 Esistono diversi modi per aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: da Excel, dalla **casella degli strumenti**di Visual Studio e dalla finestra **Origini dati** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro usando la casella Nome in Excel  
  
1.  Selezionare una o più celle da includere nell'intervallo denominato.  
  
2.  Nella casella **Nome**digitare un nome per l'intervallo e premere INVIO.  
  
     La casella **Nome** si trova accanto alla barra della formula, sopra la colonna **A** del foglio di lavoro.  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro con la Casella degli strumenti  
  
1.  Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Excel** .  
  
2.  Fare clic su <xref:Microsoft.Office.Tools.Excel.NamedRange> e trascinarlo in un foglio di lavoro.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo NamedRange** .  
  
3.  Selezionare una o più celle da includere nell'intervallo denominato.  
  
4.  Fare clic su **OK**.  
  
     Se non si vuole assegnare al controllo il nome predefinito, è possibile modificarlo nella finestra **Proprietà** .  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro con la finestra Origini dati  
  
1.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per ulteriori informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).  
  
2.  Trascinare un singolo campo dalla finestra **Origini dati** al foglio di lavoro.  
  
     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.NamedRange> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Adding NamedRange Controls at Run Time in a Document-Level Project  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a livello di codice al foglio di lavoro in fase di esecuzione e creare in questo modo i controlli host in risposta a eventi. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1`inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e impostarne la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Adding NamedRange Controls at Run Time in an VSTO Add-in project  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e ne imposta la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  