---
title: Limitazioni a livello di codice degli elementi Host e controlli Host | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c47b1158eefda91e83ce85a5a7403f3f8f0249a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Limitazioni a livello di codice degli elementi e dei controlli host
  Ogni elemento host e controllo host viene progettato per comportarsi come un oggetto nativo corrispondente di Microsoft Office Word o Microsoft Office Excel, con funzionalità aggiuntive. Tuttavia, esistono alcune differenze fondamentali tra il comportamento degli elementi host e dei controlli host e gli oggetti nativi di Office in fase di esecuzione.  
  
 Per informazioni generali sugli elementi host e sui controlli host, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-creating-host-items"></a>Creazione a livello di codice di elementi host  
 Quando si crea o si apre a livello di codice un documento, una cartella di lavoro o un foglio di lavoro in fase di esecuzione mediante il modello a oggetti di Word o Excel, l'elemento non è un elemento host. Al contrario, si tratta di un nuovo oggetto nativo di Office. Ad esempio, se si usa il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> per creare un nuovo documento di Word in fase di esecuzione, si tratterà di un oggetto <xref:Microsoft.Office.Interop.Word.Document> nativo piuttosto che di un elemento host <xref:Microsoft.Office.Tools.Word.Document> . Analogamente, quando si crea un nuovo foglio di lavoro in fase di esecuzione usando il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> , si ottiene un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo piuttosto che un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
 Nei progetti a livello di documento non è possibile creare elementi host in fase di esecuzione. Gli elementi host possono essere creati solo in fase di progettazione nei progetti a livello di documento. Per altre informazioni, vedere [Document Host Item](../vsto/document-host-item.md), [Workbook Host Item](../vsto/workbook-host-item.md)e [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
 Nei progetti di componente aggiuntivo VSTO è possibile creare elementi host <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>o <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-creating-host-controls"></a>Creazione a livello di codice di controlli host  
 È possibile aggiungere a livello di codice controlli host a un elemento host <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Non è possibile aggiungere controlli host a un oggetto <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>nativo.  
  
> [!NOTE]  
>  I controlli host seguenti non possono essere aggiunti a livello di codice a fogli di lavoro o documenti: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>e <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understanding-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Informazioni sulle differenze di tipo tra elementi host, controlli host e oggetti nativi di Office  
 Per ogni elemento host e controllo host esiste un oggetto nativo di Microsoft Office Word o Microsoft Office Excel sottostante. È possibile accedere all'oggetto sottostante usando la proprietà InnerObject dell'elemento host o del controllo host. Non esiste tuttavia alcun modo per eseguire il cast di un oggetto nativo di Office nel corrispondente elemento host o controllo host. Se si prova a eseguire il cast di un oggetto nativo di Office nel tipo di un elemento host o di un controllo host, verrà generata un'eccezione <xref:System.InvalidCastException> .  
  
 Esistono diversi scenari in cui le differenze tra i tipi di elementi host e controlli host e gli oggetti nativi di Office sottostanti possono influire sul codice.  
  
### <a name="passing-host-controls-to-methods-and-properties"></a>Passaggio di controlli host a metodi e proprietà  
 In Word non è possibile passare un controllo host a un metodo o a una proprietà che richiede un oggetto nativo di Word come parametro. È necessario utilizzare la proprietà InnerObject del controllo host per restituire l'oggetto nativo di Word sottostante. Ad esempio, è possibile passare un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> a un metodo passando la proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> del controllo host <xref:Microsoft.Office.Tools.Word.Bookmark> al metodo.  
  
 In Excel, è necessario utilizzare la proprietà InnerObject del controllo host per passare il controllo host a un metodo o proprietà quando il metodo o la proprietà prevede l'oggetto di Excel sottostante.  
  
 L'esempio seguente crea un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e lo passa al metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . Il codice usa la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> dell'intervallo denominato per restituire l'oggetto <xref:Microsoft.Office.Interop.Excel.Range> di Office sottostante richiesto dal metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Tipi restituiti delle proprietà e dei metodi nativi di Office  
 La maggior parte dei metodi e delle proprietà degli elementi host restituisce l'oggetto nativo di Office sottostante sul quale si basa l'elemento host. Ad esempio, la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> di un controllo host <xref:Microsoft.Office.Tools.Excel.NamedRange> in Excel restituisce un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> piuttosto che un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> . Analogamente, la proprietà <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> di un controllo host <xref:Microsoft.Office.Tools.Word.RichTextContentControl> in Word restituisce un oggetto <xref:Microsoft.Office.Interop.Word.Document> piuttosto che un elemento host <xref:Microsoft.Office.Tools.Word.Document> .  
  
### <a name="accessing-collections-of-host-controls"></a>Accesso alle raccolte di controlli host  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non fornisce raccolte specifiche per ogni tipo di controllo host. In alternativa, utilizzare la proprietà di controlli di un elemento host per scorrere tutti i controlli gestiti (controlli host e controlli Windows Form) nel documento o foglio di lavoro e quindi cercare gli elementi che corrispondono al tipo del controllo host che si è interessati. L'esempio di codice seguente esamina ogni controllo in un documento di Word e determina se il controllo è di tipo <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Per ulteriori informazioni sulla proprietà di controlli di elementi host, vedere [aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 I modelli a oggetti di Word ed Excel includono proprietà che espongono raccolte di controlli nativi in documenti e fogli di lavoro. Non è possibile accedere ai controlli gestiti tramite queste proprietà. Ad esempio, non è possibile enumerare ogni controllo host <xref:Microsoft.Office.Tools.Word.Bookmark> in un documento tramite la proprietà <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Document> o la proprietà <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Document>. Queste proprietà includono solo i controlli <xref:Microsoft.Office.Interop.Word.Bookmark> nel documento; non contengono i controlli host <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Elemento Host Worksheet](../vsto/worksheet-host-item.md)   
 [Elemento Host cartella di lavoro](../vsto/workbook-host-item.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
  
  