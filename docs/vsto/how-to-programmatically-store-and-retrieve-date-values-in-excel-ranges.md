---
title: 'Procedura: archiviare a livello di codice e recuperare valori di data in intervalli di Excel | Documenti Microsoft'
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
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 589079a593400549a69940fc42d1cf25fcab8826
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Procedura: memorizzare e recuperare valori di data in intervalli di Excel a livello di codice
  È possibile archiviare e recuperare i valori in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Se si archivia un valore di data che cade il o dopo il 1/1/1900 in un intervallo con gli strumenti di sviluppo per Office in Visual Studio, archiviato nel formato di automazione OLE (OA). È necessario utilizzare il <xref:System.DateTime.FromOADate%2A> metodo per recuperare il valore di date di automazione OLE (OA). Se la data è precedente a 1/1/1900, archiviato sotto forma di stringa.  
  
> [!NOTE]  
>  Le date di Excel differiscono dalle date di automazione OLE per i primi due mesi del 1900. Esistono anche differenze se il **sistema data 1904** opzione è selezionata. Gli esempi di codice riportato di seguito non consente di risolvere queste differenze.  
  
## <a name="using-a-namedrange-control"></a>Utilizzo di un controllo NamedRange  
  
-   Questo esempio è per le personalizzazioni a livello di documento. Il codice seguente deve essere inserito in una classe foglio, non nella `ThisWorkbook` classe.  
  
#### <a name="to-store-a-date-value-in-a-named-range"></a>Per archiviare un valore di data in un intervallo denominato  
  
1.  Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Impostare la data odierna come valore per `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
#### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Per recuperare un valore di data da un intervallo denominato  
  
1.  Recuperare il valore di data da `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="using-native-excel-ranges"></a>Utilizzo di intervalli di Excel nativo  
  
#### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Per archiviare un valore di data in un oggetto intervallo di Excel nativo  
  
1.  Creare un <xref:Microsoft.Office.Interop.Excel.Range> che rappresenta una cella **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Impostare la data odierna come valore per `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
#### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Per recuperare un valore di data da un oggetto intervallo di Excel nativo  
  
1.  Recuperare il valore di data da `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Panoramica del modello oggetto di Excel](../vsto/excel-object-model-overview.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Procedura: fare riferimento a livello di programmazione agli intervalli del foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  