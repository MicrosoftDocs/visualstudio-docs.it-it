---
title: 'Procedura: aggiungere righe e colonne alle tabelle di Word | Documenti Microsoft'
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
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bcad8104f5267f86c6538077f6f53abbac986d52
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice
  In una tabella di Microsoft Office Word le celle sono organizzate in righe e colonne. È possibile usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Rows> per aggiungere righe alla tabella e il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Columns> per aggiungere colonne.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Esempi di personalizzazione a livello di documento  
 Gli esempi di codice seguenti possono essere usati in una personalizzazione a livello di documento. Per usare questi esempi, eseguirli dalla classe `ThisDocument` nel progetto. Gli esempi presuppongono che il documento associato alla personalizzazione contenga già almeno una tabella.  
  
> [!IMPORTANT]  
>  Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:  
>   
>  -   Documento di Word 2013  
> -   Modello di Word 2013  
> -   Documento di Word 2010  
> -   Modello di Word 2010  
>   
>  Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento di **Interop** assembly, quindi è necessario utilizzare le classi da tale assembly per aggiungere righe e colonne alle tabelle. Per ulteriori informazioni, vedere [come: destinazione applicazioni tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'Assembly di interoperabilità primario di Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Esempi di componente aggiuntivo VSTO  
 Gli esempi di codice seguenti possono essere usati in un componente aggiuntivo VSTO. Per usare gli esempi, eseguirli dalla classe `ThisAddIn` nel progetto. Gli esempi presuppongono che il documento attivo contenga già almeno una tabella.  
  
> [!IMPORTANT]  
>  Questo codice viene eseguito solo in progetti creati usando modelli di componente aggiuntivo VSTO per Word.  
>   
>  Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento di **Interop** assembly, quindi è necessario utilizzare le classi da tale assembly per aggiungere righe e colonne alle tabelle. Per ulteriori informazioni, vedere [come: destinazione applicazioni tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'Assembly di interoperabilità primario di Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creazione di tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md)   
 [Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Procedura: Popolare tabelle di Word con le proprietà documento a livello di codice](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  