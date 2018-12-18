---
title: Controllo del grafico | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c473c026f5d5f9a5919626fb667994e6ffdc01f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="chart-control"></a>Chart Control
  Il controllo <xref:Microsoft.Office.Tools.Excel.Chart> è un oggetto grafico che espone eventi. Quando si aggiunge un grafico a un foglio di lavoro, Visual Studio crea un oggetto <xref:Microsoft.Office.Tools.Excel.Chart> su cui è possibile programmare direttamente senza dover passare attraverso il modello a oggetti di Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Creazione del controllo  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.Chart> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione oppure in fase di esecuzione in un progetto a livello di documento.  
  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.Chart> a un foglio di lavoro in fase di esecuzione in un componente aggiuntivo VSTO. Per ulteriori informazioni, vedere [procedura: aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Gli oggetti grafico creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene chiuso. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Formattazione  
 Tutta la formattazione che può essere applicata a un oggetto <xref:Microsoft.Office.Interop.Excel.Chart> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Excel.Chart>. Sono inclusi bordi, tipi di carattere, tipo di grafico, griglie, legenda ed etichette dati.  
  
## <a name="events"></a>Eventi  
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Excel.Chart>:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Procedura: aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  