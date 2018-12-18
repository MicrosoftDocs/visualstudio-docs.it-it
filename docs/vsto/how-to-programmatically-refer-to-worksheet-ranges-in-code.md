---
title: 'Procedura: fare riferimento a livello di programmazione agli intervalli del foglio di lavoro nel codice | Documenti Microsoft'
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
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 001efb4609059ba68a0a6a5f9c30d2f416805013
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Procedura: fare riferimento agli intervalli dei fogli di lavoro nel codice a livello di codice
  Utilizzare un processo simile per fare riferimento al contenuto di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Utilizzo di un controllo NamedRange  
 L'esempio seguente aggiunge un <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro e quindi aggiunge il testo alla cella nell'intervallo.  
  
#### <a name="to-refer-to-a-namedrange-control"></a>Per fare riferimento a un controllo NamedRange  
  
1.  Assegnare una stringa per il <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> proprietà del <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>Utilizzo di intervalli di Excel nativo  
 Nell'esempio seguente aggiunge un intervallo di Excel nativo a un foglio di lavoro e quindi aggiunge il testo alla cella nell'intervallo.  
  
#### <a name="to-refer-to-a-native-range-object"></a>Per fare riferimento a un oggetto intervallo nativo  
  
1.  Assegnare una stringa per il <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> proprietà dell'intervallo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Procedura: a livello di codice il controllo ortografico nei fogli di lavoro](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Procedura: a livello di programmazione applicare stili agli intervalli nelle cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: riempire automaticamente a livello di codice gli intervalli con dati modificati in modo incrementale](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Procedura: eseguire la ricerca a livello di codice per il testo negli intervalli del foglio di lavoro](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  