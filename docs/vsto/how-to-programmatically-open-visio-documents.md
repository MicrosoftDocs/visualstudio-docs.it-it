---
title: 'Procedura: aprire documenti di Visio | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b5a837b4b12420c65817b6dfb156e0fe47fcdba6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-visio-documents"></a>Procedura: Aprire documenti di Visio a livello di codice
  Esistono due metodi per l'apertura di documenti di Microsoft Office Visio esistenti: Open e OpenEx. Il metodo OpenEx è identico al metodo di apertura, ad eccezione del fatto che fornisca gli argomenti in cui il chiamante può specificare la modalità di apertura del documento.  
  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) e [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) .  
  
## <a name="opening-a-visio-document"></a>Apertura di un documento di Visio  
  
#### <a name="to-open-a-visio-document"></a>Per aprire un documento di Visio  
  
-   Chiamare il metodo Interop e fornire il percorso completo del documento di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>Aprire un documento di Visio con gli argomenti specificati  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Per aprire un documento di Visio di sola lettura e come ancorato  
  
-   Chiamare l'OpenEx, specificare il percorso completo del documento di Visio e includere gli argomenti che si desidera utilizzare, in questo caso, ancorato e sola lettura.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Deve essere presente un documento di Visio denominato `myDrawing.vsd` in una directory denominata `Test` nella cartella Documenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: creare nuovi documenti di Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: chiudere a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: a livello di programmazione salvare documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  