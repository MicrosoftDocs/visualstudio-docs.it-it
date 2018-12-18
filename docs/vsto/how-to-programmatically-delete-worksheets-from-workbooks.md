---
title: 'Procedura: eliminare a livello di codice i fogli di lavoro dalle cartelle di lavoro | Documenti Microsoft'
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
- workbooks, deleting worksheets
- worksheets, deleting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 05910578569399534f2377c0960f3af8e0054625
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Procedura: eliminare fogli di lavoro da una cartella di lavoro a livello di codice
  È possibile eliminare qualsiasi foglio di lavoro da una cartella di lavoro. Per eliminare un foglio di lavoro, usare l'elemento host del foglio di lavoro o accedere al foglio di lavoro tramite la raccolta Sheets della cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>Uso dell'elemento host Worksheet  
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per eliminarlo usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>. Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento direttamente all'elemento host del foglio di lavoro.  
  
> [!IMPORTANT]  
>  Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:  
>   
>  -   Cartella di lavoro di Excel 2013  
> -   Modello di Excel 2013  
> -   Cartella di lavoro di Excel 2010  
> -   Modello di Excel 2010  
>   
>  Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento di **Interop** assembly, quindi è necessario usare le classi da tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per ulteriori informazioni, vedere [come: destinazione applicazioni tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento agli Assembly di interoperabilità primario di Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Per eliminare un foglio di lavoro mediante un elemento host del foglio di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> di `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Uso della raccolta Sheets della cartella di lavoro di Excel  
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:  
  
-   Se si intende eliminare un foglio di lavoro in un componente aggiuntivo VSTO.  
  
-   Se il foglio di lavoro che si vuole eliminare è stato creato in fase di esecuzione in una personalizzazione a livello di documento.  
  
 Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento alla pagina mediante il numero di indice di **fogli** insieme. Per questo codice si presume che sia già stato creato un nuovo foglio di lavoro a livello di codice.  
  
> [!IMPORTANT]  
>  Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento di **Interop** assembly, quindi è necessario usare le classi da tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per ulteriori informazioni, vedere [come: destinazione applicazioni tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento agli Assembly di interoperabilità primario di Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Per eliminare un foglio di lavoro mediante la raccolta Sheets della cartella di lavoro di Excel  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Procedura: spostare fogli di lavoro all'interno di cartelle di lavoro](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Procedura: selezionare a livello di codice i fogli di lavoro](../vsto/how-to-programmatically-select-worksheets.md)   
 [Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Elemento Host Worksheet](../vsto/worksheet-host-item.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  