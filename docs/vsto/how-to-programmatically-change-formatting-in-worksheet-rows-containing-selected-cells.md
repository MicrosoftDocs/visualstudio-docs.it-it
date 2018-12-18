---
title: 'Procedura: modificare a livello di codice la formattazione nelle righe del foglio di lavoro contenenti celle selezionate | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35f0475a15b41b63b99c08a90ebbf724b0adaed8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Procedura: modificare la formattazione nelle righe di un foglio di lavoro contenenti celle selezionate a livello di codice
  È possibile modificare il tipo di carattere di un'intera riga che contiene una cella selezionata in modo che il testo in grassetto.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>Per visualizzare la riga corrente in grassetto e in precedenza in grassetto riga normale  
  
1.  Dichiarare una variabile statica per tenere traccia della riga selezionata in precedenza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#37)]  
  
2.  Recuperare un riferimento alla cella corrente tramite il <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> proprietà.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#38)]  
  
3.  Stile corrente riga in grassetto, usando il <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> proprietà della cella attiva.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#39)]  
  
4.  Assicurarsi che il valore corrente di `previousRow` è non da 0. 0 (zero) indica che questa è la prima volta tramite codice.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#40)]  
  
5.  Verificare che la riga corrente è diversa dalla riga precedente.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#41)]  
  
6.  Recupera un riferimento a un intervallo che rappresenta la riga selezionata in precedenza e set che non sia di riga in grassetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#42)]  
  
7.  Archiviare la riga corrente in modo che possa diventare la riga precedente il passaggio successivo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#43)]  
  
 L'esempio seguente mostra il metodo completo.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#36)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: a livello di programmazione applicare stili agli intervalli nelle cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: copiare a livello di programmazione dati e formattazione nei fogli di lavoro](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  