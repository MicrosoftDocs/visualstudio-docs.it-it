---
title: 'Procedura: copiare a livello di programmazione i dati e formattazione nei fogli di lavoro | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10a710af8120ab789ec3a9c3ccb2b7e4398e82f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Procedura: copiare dati e formattazione nei fogli di lavoro a livello di codice
  È possibile copiare dati da un intervallo in un foglio di lavoro per tutti gli altri fogli in una cartella di lavoro utilizzando il <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> metodo. Specificare un intervallo, e se si desidera copiare i dati, la formattazione o entrambi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 In questo esempio richiede un intervallo denominato `rangeData` in un foglio di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Procedura: modificare a livello di codice la formattazione nelle righe del foglio di lavoro contenenti celle selezionate](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  