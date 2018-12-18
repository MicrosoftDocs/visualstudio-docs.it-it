---
title: 'Procedura: riempire controlli ListObject con dati | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 433928cd817e3ef796d9f6e2f4b4aab27cda2346
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Procedura: Riempire controlli ListObject con dati
  È possibile usare il data binding per aggiungere rapidamente dati al documento. Dopo aver associato i dati a un oggetto elenco, è possibile disconnetterlo in modo che visualizzi i dati senza tuttavia essere più associato all'origine dati.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [modalità per creare un elenco in Excel connesso a un elenco SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
### <a name="to-bind-data-to-a-listobject-control"></a>Per associare dati a un controllo ListObject  
  
1.  Creare un oggetto <xref:System.Data.DataTable> a livello di classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]  
  
2.  Aggiungere colonne e dati di esempio nel gestore eventi `Startup` della classe `Sheet1` (in un progetto a livello di documento) oppure della classe `ThisAddIn` (in un progetto a livello di applicazione).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]  
  
3.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. 'ordine delle colonne nell'oggetto elenco può differire dall'ordine in cui vengono visualizzate nell'oggetto <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]  
  
### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Per disconnettere il controllo ListObject dall'origine dati  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> di `List1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: eseguire il mapping delle colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject (controllo)](../vsto/listobject-control.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura: popolare fogli di lavoro con dati da un Database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Procedura: Popolare documenti con dati specificati da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  