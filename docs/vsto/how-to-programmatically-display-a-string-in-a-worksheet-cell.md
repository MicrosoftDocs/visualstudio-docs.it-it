---
title: 'Procedura: visualizzare a livello di codice una stringa in una cella di foglio di lavoro | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29dafd7a3eace9350bdb045b2aee0d90a92a445c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Procedura: visualizzare una stringa in una cella del foglio di lavoro a livello di codice
  In questo esempio viene illustrato come visualizzare il testo in una cella a livello di codice. Per visualizzare il testo nella cella, utilizzare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Utilizzo di un controllo NamedRange  
 Questo esempio viene utilizzato un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `message`. Il controllo deve essere aggiunto a una personalizzazione a livello di documento in fase di progettazione. Il codice seguente deve essere inserito in una classe foglio, non nella `ThisWorkbook` classe.  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>Per visualizzare il testo in un controllo NamedRange  
  
1.  Impostare il valore della <xref:Microsoft.Office.Tools.Excel.NamedRange> il controllo a **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>Utilizzo di un intervallo di Excel nativo  
 Il codice seguente crea un nuovo intervallo a livello di codice e quindi assegna un valore.  
  
#### <a name="to-display-text-in-an-excel-range"></a>Per visualizzare il testo in un intervallo di Excel  
  
1.  Recuperare l'intervallo in corrispondenza della cella **A1** su `Sheet1` e impostare il valore su **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Raccolta dati utilizzando un Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Risoluzione dei problemi delle soluzioni Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  