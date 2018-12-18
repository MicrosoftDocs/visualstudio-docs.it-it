---
title: 'Procedura: eseguire il mapping delle colonne ListObject ai dati | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 370f82c6a167a9747a3a41ac3720bc4f679fb8d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-listobject-columns-to-data"></a>Procedura: Eseguire il mapping delle colonne ListObject ai dati
  Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un oggetto <xref:System.Data.DataTable>, è possibile che non si voglia visualizzare tutte le colonne in un elenco o che alcune colonne non siano associate a dati. È possibile mappare le colonne da visualizzare nel <xref:Microsoft.Office.Tools.Excel.ListObject> quando si chiama il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [modalità per creare un elenco in Excel connesso a un elenco SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="mapping-columns"></a>Mapping di colonne  
  
#### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Per mappare una tabella dati alle colonne in un elenco  
  
1.  Creare l'oggetto <xref:System.Data.DataTable> a livello di classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Aggiungere colonne e dati di esempio nel gestore eventi `Startup` della classe `Sheet1` (in un progetto a livello di documento) oppure della classe `ThisAddIn` (in un progetto di componente aggiuntivo VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. L'oggetto elenco verrà associato all'oggetto <xref:System.Data.DataTable>appena creato, ma l'ordine delle colonne nell'oggetto elenco sarà diverso dall'ordine in cui sono visualizzate nell'oggetto <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specifying-unmapped-columns"></a>Definizione delle colonne non mappate  
 Quando si mappano le colonne a un oggetto <xref:System.Data.DataTable>, si può anche specificare che alcune colonne non devono essere associate a dati passando una stringa vuota. Viene quindi aggiunta una nuova colonna non associata a dati al controllo <xref:Microsoft.Office.Tools.Excel.ListObject> .  
  
#### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Per specificare una colonna non mappata durante il mapping delle colonne ListObject  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. Usare una stringa vuota per indicare dove viene aggiunta una colonna non mappata, in questo caso tra la colonna del titolo e la colonna del cognome.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: riempire controlli ListObject con dati](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controllo ListObject](../vsto/listobject-control.md)  
  
  