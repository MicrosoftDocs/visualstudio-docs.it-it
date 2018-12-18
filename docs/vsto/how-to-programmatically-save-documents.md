---
title: 'Procedura: salvare i documenti a livello di codice | Documenti Microsoft'
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
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 68bf8450906dae3faf5f62acd2d057718938b520
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-documents"></a>Procedura: salvare documenti a livello di codice
  Esistono diversi modi per salvare i documenti di Microsoft Office Word. È possibile salvare un documento senza modificare il nome del documento, oppure è possibile salvare un documento con un nuovo nome.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>Salvataggio di un documento senza modificare il nome  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Per salvare il documento associato a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Save%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>Per salvare il documento attivo  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodo per il documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 Se non sei sicuro che il documento che si desidera salvare sia il documento attivo, è possibile fare riferimento a esso in base al nome.  
  
#### <a name="to-save-a-document-specified-by-name"></a>Per salvare un documento specificato in base al nome  
  
1.  Utilizzare il nome del documento come argomento per il <xref:Microsoft.Office.Interop.Word.Documents> insieme. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Salvataggio di un documento con un nuovo nome  
 Utilizzare il metodo SaveAs per salvare un documento con un nuovo nome. È possibile utilizzare questo metodo per il <xref:Microsoft.Office.Tools.Word.Document> elemento host in un progetto di Word a livello di documento o di nativo <xref:Microsoft.Office.Interop.Word.Document> oggetto in qualsiasi progetto di Word. Questo metodo richiede che si specifica il nuovo nome file, ma gli altri argomenti sono facoltativi.  
  
> [!NOTE]  
>  Se si visualizza il **SaveAs** all'interno della finestra di dialogo di <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> gestore dell'evento di `ThisDocument` e impostare il *Annulla* parametro **false**, l'applicazione potrebbe chiudere in modo imprevisto. Se si imposta la *Annulla* parametro **true**, viene visualizzato un messaggio di errore che indicherà che è stata disabilitata.  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Per salvare il documento associato a una personalizzazione a livello di documento con un nuovo nome  
  
1.  Chiamare il <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metodo la `ThisDocument` classe nel progetto, con un nome di file e percorso completo. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` .  
  
    > [!NOTE]  
    >  Il <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metodo genera un'eccezione se una directory di destinazione non esiste o se sono presenti altri problemi di salvataggio di un file. È consigliabile utilizzare un **try … catch** bloccare tutto il <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metodo o all'interno di un metodo chiamante.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>Per salvare un documento nativo con un nuovo nome  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo il <xref:Microsoft.Office.Interop.Word.Document> che si vuole salvare usando un nome di file e percorso completo. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.  
  
     Esempio di codice seguente salva il documento attivo con un nuovo nome. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo genera un'eccezione se una directory di destinazione non esiste o se sono presenti altri problemi di salvataggio di un file. È consigliabile utilizzare un **try … catch** bloccare tutto il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo o all'interno di un metodo chiamante.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Per salvare un documento in base al nome, un documento denominato NewDocument. doc deve essere presente in una directory denominata Test sull'unità C.  
  
-   Per salvare un documento con un nuovo nome, una directory denominata Test deve essere presente nell'unità C.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: chiudere i documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)   
 [Procedura: aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Elemento Host documento](../vsto/document-host-item.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  