---
title: 'Procedura: aggiungere a livello di programmazione di intestazioni e piè di pagina ai documenti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fdd64c59acd3c3e9521f899bcdb61e83fa4da29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Procedura: aggiungere intestazioni e piè di pagina ai documenti a livello di codice
  È possibile aggiungere testo alle intestazioni e ai piè di pagina del documento usando la proprietà <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> e la proprietà <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> di <xref:Microsoft.Office.Interop.Word.Section>. Ogni sezione di un documento contiene tre intestazioni e piè di pagina:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Le procedure sono diverse per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>personalizzazioni a livello di documento  
 Per usare gli esempi di codice seguenti, eseguirli dalla classe `ThisDocument` nel progetto.  
  
#### <a name="to-add-text-to-footers-in-the-document"></a>Per aggiungere testo ai piè di pagina nel documento  
  
1.  L'esempio di codice seguente imposta il tipo di carattere del testo da inserire nel piè di pagina principale di ogni sezione del documento e quindi inserisce il testo nel piè di pagina.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Per aggiungere testo alle intestazioni nel documento  
  
1.  L'esempio di codice seguente aggiunge un campo per mostrare il numero di pagina in ogni intestazione del documento e quindi imposta l'allineamento del paragrafo in modo che il testo venga allineato a destra dell'intestazione.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>VSTO Add-ins  
 Per usare gli esempi di codice seguenti, eseguirli dalla classe `ThisAddIn` nel progetto.  
  
#### <a name="to-add-text-to-footers-in-a-document"></a>Per aggiungere testo ai piè di pagina in un documento  
  
1.  L'esempio di codice seguente imposta il tipo di carattere del testo da inserire nel piè di pagina principale di ogni sezione del documento e quindi inserisce il testo nel piè di pagina. L'esempio di codice usa il documento attivo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Per aggiungere testo alle intestazioni nel documento  
  
1.  L'esempio di codice seguente aggiunge un campo per mostrare il numero di pagina in ogni intestazione del documento e quindi imposta l'allineamento del paragrafo in modo che il testo venga allineato a destra dell'intestazione. L'esempio di codice usa il documento attivo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creazione di nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)   
 [Procedura: estendere gli intervalli nei documenti](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: Riprodurre a ciclo continuo gli elementi trovati nei documenti a livello di codice](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   