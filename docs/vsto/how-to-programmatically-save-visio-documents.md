---
title: 'Procedura: salvare a livello di programmazione di documenti di Visio | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7a98ff5a7b7df6e2e609ac2d3bf89d7fd4b23648
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-visio-documents"></a>Procedura: Salvare documenti di Visio a livello di codice
  Esistono varie modalità per salvare documenti di Microsoft Office Visio:  
  
-   Salvare le modifiche in un documento esistente.  
  
-   Salvare un nuovo documento oppure salvare un documento con un nuovo nome.  
  
-   Salvare un documento con gli argomenti specificati.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA per i metodi [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) e [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="saving-an-existing-document"></a>Salvataggio un documento esistente  
  
#### <a name="to-save-a-document"></a>Per salvare un documento  
  
-   Chiamare il metodo Save della classe Microsoft.Office.Tools.Visio.Document di un documento che è stato salvato in precedenza.  
  
     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Il metodo Save genera un'eccezione se non è ancora stato salvato un nuovo documento di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Salvataggio di un documento con un nuovo nome  
 Utilizzare il metodo di Microsoft per salvare un nuovo documento o un documento con un nuovo nome. Con questo metodo è necessario specificare il nuovo nome del file.  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Per salvare il documento attivo con un nuovo nome  
  
-   Chiamare il metodo di Microsoft di Microsoft.Office.Tools.Visio.Document che si desidera salvare usando un percorso completo include un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.  
  
     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>Salvataggio di un documento con un nuovo nome e argomenti specificati  
 Utilizzare il SaveAsEx per salvare un documento con un nuovo nome e specificare qualsiasi argomento applicabile da applicare al documento.  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Per salvare un documento con un nuovo nome e argomenti specificati  
  
-   Chiamare il SaveAsEx di Microsoft.Office.Tools.Visio.Document che si desidera salvare usando un percorso completo include un nome file. Se un file con quel nome già esiste in quella cartella, viene generata un'eccezione.  
  
     L'esempio di codice seguente salva il documento attivo con un nuovo nome, lo contrassegna come di sola lettura e visualizza il documento nell'elenco di documenti Usati di recente. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Per salvare un documento con un nuovo nome, una directory denominata `Test` deve trovarsi nella cartella Documenti (per Windows XP e versioni precedenti) oppure nella cartella Documenti (per Windows Vista).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: creare nuovi documenti di Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: chiudere a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  