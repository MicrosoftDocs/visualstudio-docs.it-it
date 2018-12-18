---
title: 'Procedura: rimuovere estensioni di codice gestito dai documenti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7a5e70db36c0cd1b99a670e13a353e15f7558e7e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Procedura: rimuovere estensioni di codice gestito dai documenti
  Rimuovere l'assembly di personalizzazione a livello di codice da un documento o una cartella di lavoro che fa parte di una personalizzazione a livello di documento per Microsoft Office Word o Microsoft Office Excel. Gli utenti possono quindi aprire i documenti e visualizzare il contenuto, ma qualsiasi interfaccia utente personalizzata (UI) aggiunta ai documenti non verrà visualizzati e non verrà eseguito il codice.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È possibile rimuovere l'assembly di personalizzazione utilizzando uno dei metodi RemoveCustomization forniti dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Il metodo da utilizzare varia a seconda se si desidera rimuovere la personalizzazione in fase di esecuzione (ovvero, eseguendo il codice nella personalizzazione quando la parola documento o cartella di lavoro di Excel è aperto), o se si desidera rimuovere la personalizzazione da un documento chiuso o un documento che i s in un server che non è installato Microsoft Office.  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [come ricerca per categorie: allegare o scollegamento di un Assembly di VSTO da un documento di Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>Per rimuovere l'assembly di personalizzazione in fase di esecuzione  
  
1.  Nel codice della personalizzazione, chiamare il <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> (metodo) (per Word) o <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> (per Excel). Questo metodo deve essere chiamato solo dopo la personalizzazione non è più necessario.  
  
     In cui viene chiamato questo metodo nel codice dipende dal modo in cui viene utilizzata la personalizzazione. Ad esempio, se i clienti utilizzano le funzionalità della personalizzazione finché sono pronti per inviare il documento ad altri client che devono solo il documento e non la personalizzazione, è possibile fornire un'interfaccia utente che chiama RemoveCustomization quando il cliente fa clic sopra. In alternativa, se la personalizzazione popola il documento con dati quando è aperto, ma la personalizzazione non fornisce altre funzionalità che sono accessibili direttamente dai clienti, quindi è possibile chiamare RemoveCustomization non appena la personalizzazione al termine dell'inizializzazione del documento.  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Per rimuovere l'assembly di personalizzazione da un documento chiuso o un documento in un server  
  
1.  In un progetto Windows Form o un progetto che non richiede Microsoft Office, ad esempio un'applicazione console, aggiungere un riferimento all'assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Aggiungere il seguente **importazioni** o **utilizzando** all'inizio del file di codice.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metodo il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> e specificare il percorso del documento della soluzione per il parametro.  
  
     Esempio di codice seguente presuppone che si stia rimuovendo la personalizzazione da un documento denominato **WordDocument1.docx** che si trova sul desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera rimuovere la personalizzazione. Il computer deve disporre di Visual Studio 2010 Tools per Office Runtime installato.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di documenti in un Server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Procedura: Associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  