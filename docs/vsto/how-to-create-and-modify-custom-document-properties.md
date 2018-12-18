---
title: 'Procedura: creare e modificare le proprietà personalizzate dei documenti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c997fbe764ba355d16def278c9beda8c177faed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Procedura: Creare e modificare proprietà personalizzate di un documento
  Le applicazioni di Microsoft Office elencate in precedenza forniscono proprietà incorporate che vengono archiviate con i documenti. Inoltre, è possibile creare e modificare le proprietà personalizzate del documento se si vuole archiviare informazioni aggiuntive con il documento.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Utilizzare la proprietà CustomDocumentProperties di un documento per lavorare con le proprietà personalizzate. Ad esempio, in un progetto a livello di documento per Microsoft Office Excel, usare la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> della classe `ThisWorkbook` . In un progetto di componente aggiuntivo VSTO per Excel, usare la proprietà <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> . Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.  
  
 Nell'esempio seguente viene illustrato come aggiungere una proprietà personalizzata in una personalizzazione a livello di documento per Excel e come assegnare un valore a tale proprietà.  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [procedura: accedere e modificare le proprietà di documento personalizzato in Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Esempio  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Il tentativo di accesso alla proprietà `Value` per proprietà non definite genera un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedura: Leggere e scrivere nelle proprietà dei documenti](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  