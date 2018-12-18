---
title: 'Procedura: aggiungere controlli ListObject a fogli di lavoro | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55d3a26f0fbf02556071dfc16d08357519b5cff9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Procedura: Aggiungere controlli ListObject a fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione nei progetti di componente aggiuntivo VSTO.  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli ListObject in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per altre informazioni sui controlli <xref:Microsoft.Office.Tools.Excel.ListObject> , vedere [ListObject Control](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Adding ListObject Controls at Design Time  
 Esistono diversi modi per aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: da Excel, dalla **casella degli strumenti**di Visual Studio e dalla finestra **Origini dati** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-use-the-ribbon-in-excel"></a>Per usare la barra multifunzione in Excel  
  
1.  Nel gruppo **Tabelle** della scheda **Inserisci** fare clic su **Tabella**.  
  
2.  Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.  
  
#### <a name="to-use-the-toolbox"></a>Per usare la casella degli strumenti  
  
1.  Dalla scheda **Controlli Excel** della **casella degli strumenti**trascinare <xref:Microsoft.Office.Tools.Excel.ListObject> nel foglio di lavoro.  
  
     Viene visualizzata la finestra di dialogo **Aggiungi controllo ListObject** .  
  
2.  Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.  
  
     Per modificare il nome predefinito, usare la finestra **Proprietà** .  
  
#### <a name="to-use-the-data-sources-window"></a>Per usare la finestra Origini dati  
  
1.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per ulteriori informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).  
  
2.  Trascinare una tabella dalla finestra **Origini dati** al foglio di lavoro.  
  
     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.ListObject> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Adding ListObject Controls at Run Time in a Document-Level Project  
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in modo dinamico in fase di esecuzione e creare in questo modo i controlli host in risposta a eventi. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro è chiuso. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1`inserire il codice seguente per aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Adding ListObject Controls at Run Time in an VSTO Add-in project  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene salvato e chiuso. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [ListObject (controllo)](../vsto/listobject-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  