---
title: 'Procedura: aggiungere forme a un documento di Visio | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1cc4369977e1989960fe9448d4dd7d56e67ed7a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Procedura: Aggiungere forme a un documento di Visio a livello di codice
  È possibile aggiungere forme a un documento di Microsoft Office Visio recuperando i master da uno stencil e rilasciando le forme nella pagina attiva.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA per il metodo [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) , la proprietà [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) e il metodo [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) .  
  
## <a name="adding-shapes-to-a-visio-document"></a>Aggiunta di forme a un documento di Visio  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>Per aggiungere forme a un documento di Visio  
  
-   Con un documento attivo, recuperare i master dalla raccolta Documents.Masters e rilasciare le forme nel documento attivo. È possibile recuperare un master usando l'indice o il nome del master.  
  
     L'esempio di codice seguente crea un documento di Visio vuoto e quindi lo apre con lo stencil **Forme base** ancorato. Il codice recupera quindi diverse forme e le inserisce nella pagina attiva.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Utilizzo delle forme di Visio](../vsto/working-with-visio-shapes.md)   
 [Procedura: Copiare e incollare forme in un documento di Visio a livello di codice](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  