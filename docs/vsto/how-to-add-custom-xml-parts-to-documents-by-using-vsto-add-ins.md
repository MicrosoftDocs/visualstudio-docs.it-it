---
title: 'Procedura: aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d06918a9b1d2bf1bec3f39d3e58352665d07e5c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Procedura: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO
  È possibile archiviare dati XML nei tipi seguenti di documenti creando una parte XML personalizzata in un componente aggiuntivo VSTO:  
  
-   Cartella di lavoro di Microsoft Office Excel.  
  
-   Documento di Microsoft Office Word.  
  
-   Presentazione di Microsoft Office PowerPoint.  
  
 Per altre informazioni, vedere [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
 **Si applica a:** le informazioni contenute in questo argomento si applicano ai progetti a livello di applicazione per Excel, PowerPoint e Word. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel  
  
1.  Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> della cartella di lavoro. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella cartella di lavoro.  
  
     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a una cartella di lavoro specificata.  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  Aggiungere il metodo `AddCustomXmlPartToWorkbook` alla classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
3.  Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre una cartella di lavoro, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> .  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Per aggiungere una parte XML personalizzata a un documento di Word  
  
1.  Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> del documento. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nel documento.  
  
     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a un documento specificato.  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  Aggiungere il metodo `AddCustomXmlPartToDocument` alla classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Word.  
  
3.  Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre un documento, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .  
  
### <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Per aggiungere una parte XML personalizzata a una presentazione di PowerPoint  
  
1.  Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> della presentazione. L'oggetto <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella presentazione.  
  
     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a una presentazione specificata.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  Aggiungere il metodo `AddCustomXmlPartToPresentation` alla classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per PowerPoint.  
  
3.  Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre una presentazione, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> .  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Per semplicità, in questo esempio viene usata una stringa XML definita come variabile locale nel metodo. In genere, è necessario ottenere l'XML da un'origine esterna, ad esempio un file o un database.  
  
## <a name="see-also"></a>Vedere anche  
 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)   
 [Procedura: Aggiungere Web part XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  