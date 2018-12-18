---
title: "Procedura: leggere e scrivere nelle proprietà dei documenti | Documenti Microsoft"
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
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1e2ac54009872aa8886b201007b60ec329a40a39
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Procedura: Leggere e scrivere nelle proprietà dei documenti
  È possibile archiviare le proprietà del documento insieme a un documento. Le applicazioni di Office offrono svariate proprietà predefinite, ad esempio autore, titolo e oggetto. Questo argomento illustra come impostare le proprietà dei documenti in Microsoft Office Excel e Microsoft Office Word.  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [procedura: accedere e modificare proprietà personalizzate dei documenti in Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="setting-document-properties-in-excel"></a>Impostazione delle proprietà dei documenti in Excel  
 Per usare le proprietà predefinite in Excel, configurare le proprietà seguenti:  
  
-   In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> della classe `ThisWorkbook` .  
  
-   In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> .  
  
 Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.  
  
 L'esempio di codice seguente illustra come modificare la proprietà predefinita **Revision Number** in un progetto a livello di documento.  
  
#### <a name="to-change-the-revision-number-property-in-excel"></a>Per modificare la proprietà Numero revisione in Excel  
  
1.  Assegnare le proprietà predefinite del documento a una variabile.  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  Incrementare di uno la proprietà `Revision Number` .  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="setting-document-properties-in-word"></a>Impostazione delle proprietà dei documenti in Word  
 Per usare le proprietà predefinite in Word, configurare le proprietà seguenti:  
  
-   In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> della classe `ThisDocument` .  
  
-   In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.  
  
 L'esempio di codice seguente illustra come modificare la proprietà predefinita **Subject** in un progetto a livello di documento.  
  
#### <a name="to-change-the-subject-property"></a>Per modificare la proprietà Oggetto  
  
1.  Assegnare le proprietà predefinite del documento a una variabile.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  Modificare la proprietà `Subject` in "White paper".  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Questo esempio presuppone che il codice della classe `ThisWorkbook` sia stato scritto in un progetto a livello di documento per Excel e quello della classe `ThisDocument` in un progetto a livello di documento per Word.  
  
 Anche se si usano Word ed Excel e i rispettivi oggetti, Microsoft Office fornisce l'elenco di proprietà predefinite disponibili per i documenti. Il tentativo di accesso a una proprietà non definita provocherà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedura: Creare e modificare proprietà personalizzate di un documento](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  