---
title: 'Procedura: a livello di codice vengono usati i file di cartella di lavoro di elenco | Documenti Microsoft'
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8a64f8a934e8cd7cdbbed11a87d15e795d19d0f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Procedura: elencare i file di cartelle di lavoro utilizzati di recente a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> proprietà restituisce una raccolta che contiene i nomi di tutti i file che vengono visualizzati nell'elenco dei file usati di recente di Microsoft Office Excel. La lunghezza dell'elenco varia a seconda del numero di file, che l'utente ha selezionato da mantenere. È possibile visualizzare i risultati in un intervallo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Per le cartelle di lavoro elenco usato di recente in un oggetto range  
  
1.  Scorrere l'elenco dei file recenti e visualizzare i nomi nelle celle relative a un <xref:Microsoft.Office.Interop.Excel.Range> oggetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  