---
title: 'Procedura: copiare a livello di codice e incollare forme in un documento di Visio | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 488cda5519a211754498b50a88995de64a8ed366
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Procedura: Copiare e incollare forme in un documento di Visio a livello di codice
  È possibile copiare a livello di codice forme contenute in una pagina di un documento e quindi incollarle in una nuova pagina dello stesso documento. Le forme possono essere incollate nella posizione predefinita (ovvero il centro della finestra attiva) o nelle stesse coordinate occupate nella pagina originale.  
  
## <a name="copying-and-pasting-shapes"></a>Operazioni di copia e incolla delle forme  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)e [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Per copiare forme nel centro di un'altra pagina  
  
-   L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nel centro della seconda pagina.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>Operazioni di copia e incolla di forme mantenendo le stesse coordinate  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)e [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
 Se si desidera controllare il formato delle informazioni incollate ed eventualmente stabilire un collegamento a un file di origine (ad esempio, un documento di Microsoft Office Word), utilizzare il metodo PasteSpecial.  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Per copiare le forme nella stessa posizione di un'altra pagina  
  
-   L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nella seconda pagina mantenendo le coordinate originali.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Utilizzo delle forme di Visio](../vsto/working-with-visio-shapes.md)   
 [Procedura: Aggiungere forme a livello di codice a un documento di Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  