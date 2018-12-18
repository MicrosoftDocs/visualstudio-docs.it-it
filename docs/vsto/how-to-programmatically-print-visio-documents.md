---
title: 'Procedura: stampa di documenti di Visio | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6efaffb9f8b3a9842528765d43f065acb314025f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-visio-documents"></a>Procedura: Stampare documenti di Visio a livello di codice
  È possibile stampare l'intero contenuto o solo una pagina specifica di un documento di Microsoft Office Visio.  
  
 Per informazioni dettagliate sui metodi di stampa, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) e [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) .  
  
## <a name="printing-a-visio-document"></a>Stampa di un documento di Visio  
  
#### <a name="to-print-a-complete-document"></a>Per stampare un documento completo  
  
-   Chiamare il metodo ai metodi dell'oggetto Microsoft che si desidera stampare.  
  
     L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>Stampa di una pagina di un documento di Visio  
  
#### <a name="to-print-a-page-of-a-document"></a>Per stampare una pagina di un documento  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Pages.Print dell'oggetto Pages che si desidera stampare.  
  
     L'esempio di codice seguente stampa la prima pagina del documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: creare nuovi documenti di Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: chiudere a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: Salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  