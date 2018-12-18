---
title: 'Procedura: aggiungere controlli Chart a fogli di lavoro | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d951b70566231db956ef8771b022937af5ee5807
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Procedura: aggiungere controlli Chart a fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.Chart> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nelle personalizzazioni a livello di documento. È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.Chart> in fase di esecuzione nei componenti aggiuntivi VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli Chart in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli Chart in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per ulteriori informazioni su <xref:Microsoft.Office.Tools.Excel.Chart> controlli, vedere [controllo Chart](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Aggiunta di controlli Chart in fase di progettazione  
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> al foglio di lavoro nello stesso modo in cui si aggiunge un grafico dall'interno dell'applicazione.  
  
> [!NOTE]  
>  Il <xref:Microsoft.Office.Tools.Excel.Chart> controllo non è disponibile il **della casella degli strumenti** o **origini dati** finestra.  
  
#### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Per aggiungere un controllo host Chart a un foglio di lavoro in Excel  
  
1.  Nel **inserire** nella scheda il **grafici** gruppo, fare clic su **colonna**, fare clic su una categoria di grafici e quindi fare clic sul tipo di grafico desiderato.  
  
2.  Nel **Inserisci grafico** la finestra di dialogo, fare clic su **OK**.  
  
3.  Nel **progettazione** nella scheda il **dati** gruppo, fare clic su **selezionare dati**.  
  
4.  Nel **Seleziona origine dati** la finestra di dialogo, fare clic il **grafico** **intervallo dati** e cancellare le selezioni predefinite.  
  
5.  Nel **dati per grafico** foglio, selezionare l'intervallo di celle contenente i dati per il grafico (celle **A5** tramite **D8**).  
  
6.  Nel **Seleziona origine dati** la finestra di dialogo, fare clic su **OK**.  
  
##  <a name="runtimedoclevel"></a> Aggiunta di controlli Chart in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> in modo dinamico in fase di esecuzione. I grafici creati dinamicamente non vengono salvati in modo permanente nel documento come controlli host quando il documento viene chiuso. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1` inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.Chart> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 I controlli Chart creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene chiuso. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host foglio di lavoro basato sul foglio di lavoro aperto e quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio prevede i requisiti seguenti:  
  
-   Dati da usare per creare il grafico, archiviati nell'intervallo da A5 a D8 nel foglio di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Chart (controllo)](../vsto/chart-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  