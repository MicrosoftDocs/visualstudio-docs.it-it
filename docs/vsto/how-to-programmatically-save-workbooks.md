---
title: 'Procedura: salvare a livello di codice le cartelle di lavoro | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4f3421c5a00d062fb49cc73b8a7f2ba592dc5d74
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-workbooks"></a>Procedura: salvare cartelle di lavoro a livello di codice
  Una cartella di lavoro può essere salvata in più modi, ad esempio senza modificare il percorso. Se si tratta del primo salvataggio della cartella di lavoro, è necessario specificare un percorso. Se non viene specificato un percorso esplicito, Microsoft Office Excel salva il file nella cartella corrente con il nome assegnato al momento della creazione. È anche possibile salvare una copia della cartella di lavoro senza modificare la cartella di lavoro aperta in memoria.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="saving-a-workbook-without-changing-the-path"></a>Salvataggio di una cartella di lavoro senza modifica del percorso  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> della classe ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> per salvare la cartella di lavoro attiva. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="saving-a-workbook-with-a-new-path"></a>Salvataggio di una cartella di lavoro con un nuovo percorso  
 È possibile salvare la cartella di lavoro specificata in un nuovo percorso o con un nuovo nome, specificando eventualmente un formato di file, una password, una modalità di accesso e altre opzioni.  
  
> [!NOTE]  
>  È possibile impostare il <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> proprietà **False** prima di salvare la cartella di lavoro con un nuovo percorso poiché per il salvataggio in alcuni formati è necessaria l'interazione. Impostando questa proprietà su **False** , in Excel utilizzare tutte le impostazioni predefinite.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> della classe `ThisWorkbook`. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> per salvare la cartella di lavoro attiva in un nuovo percorso. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="saving-a-copy-of-the-workbook"></a>Salvataggio di una copia della cartella di lavoro  
 È possibile salvare una copia della cartella di lavoro in un file senza modificare la cartella di lavoro aperta in memoria. Questa operazione è utile per creare una copia di backup senza modificare il percorso della cartella di lavoro.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> della classe `ThisWorkbook`. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> per salvare una copia della cartella di lavoro attiva. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se si annulla in modo interattivo uno dei metodi usati per salvare o copiare la cartella di lavoro, viene generato un errore di run-time nel codice. Ad esempio, se la routine chiama il <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metodo ma non di non disabilitare i prompt da Excel e l'utente fa clic su **Annulla** quando richiesto, Excel genera un errore di run-time.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Elemento Host cartella di lavoro](../vsto/workbook-host-item.md)   
 [Procedura: chiudere a livello di programmazione le cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  