---
title: 'Procedura: creazione di tabelle di Word a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a65c42f19602929b546bf105f148bf80e2d9b2db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914190"
---
# <a name="how-to-programmatically-create-word-tables"></a>Procedura: creazione di tabelle di Word a livello di codice
  La raccolta <xref:Microsoft.Office.Interop.Word.Tables> è un membro delle classi <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> e <xref:Microsoft.Office.Interop.Word.Range>, pertanto è possibile creare una tabella in ognuno di questi contenuti. Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Tables> per aggiungere una tabella nell'intervallo specificato.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="create-tables-in-document-level-customizations"></a>Creare le tabelle nelle personalizzazioni a livello di documento  
  
### <a name="to-add-a-table-to-a-document"></a>Per aggiungere una tabella a un documento  
  
- Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> per aggiungere una tabella costituita da tre righe e quattro colonne all'inizio del documento.  
  
   Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
  Quando si crea una tabella, viene aggiunta automaticamente alla raccolta <xref:Microsoft.Office.Interop.Word.Tables> dell'elemento host <xref:Microsoft.Office.Tools.Word.Document>. È quindi possibile fare riferimento alla tabella in base al numero dell'elemento usando la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, come illustrato nel codice seguente.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Per fare riferimento a una tabella in base al numero dell'elemento  
  
1. Usare la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> e fornire il numero di elemento a cui si vuole fare riferimento.  
  
    Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
   Ogni oggetto <xref:Microsoft.Office.Interop.Word.Table> dispone anche di una proprietà <xref:Microsoft.Office.Interop.Word.Table.Range%2A> che consente di impostare gli attributi di formattazione.  
  
### <a name="to-apply-a-style-to-a-table"></a>Per applicare uno stile a una tabella  
  
1.  Usare la proprietà <xref:Microsoft.Office.Interop.Word.Table.Style%2A> per applicare uno degli stili incorporati di Word a una tabella.  
  
     Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="create-tables-in-vsto-add-ins"></a>Creare tabelle nei componenti aggiuntivi VSTO  
  
### <a name="to-add-a-table-to-a-document"></a>Per aggiungere una tabella a un documento  
  
- Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> per aggiungere una tabella costituita da tre righe e quattro colonne all'inizio del documento.  
  
   L'esempio di codice seguente aggiunge una tabella al documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
  Quando si crea una tabella, viene aggiunta automaticamente alla raccolta <xref:Microsoft.Office.Interop.Word.Tables> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document>. È quindi possibile fare riferimento alla tabella in base al numero dell'elemento usando la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, come illustrato nel codice seguente.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Per fare riferimento a una tabella in base al numero dell'elemento  
  
1. Usare la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> e fornire il numero di elemento a cui si vuole fare riferimento.  
  
    L'esempio di codice seguente usa il documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
   Ogni oggetto <xref:Microsoft.Office.Interop.Word.Table> dispone anche di una proprietà <xref:Microsoft.Office.Interop.Word.Table.Range%2A> che consente di impostare gli attributi di formattazione.  
  
### <a name="to-apply-a-style-to-a-table"></a>Per applicare uno stile a una tabella  
  
1.  Usare la proprietà <xref:Microsoft.Office.Interop.Word.Table.Style%2A> per applicare uno degli stili incorporati di Word a una tabella.  
  
     L'esempio di codice seguente usa il documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere a livello di codice di testo e formattazione alle celle delle tabelle di Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Procedura: a livello di codice aggiungere righe e colonne alle tabelle di Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Procedura: a livello di codice compilare tabelle di Word con le proprietà documento](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  