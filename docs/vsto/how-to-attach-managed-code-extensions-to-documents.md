---
title: 'Procedura: associare estensioni di codice gestito a documenti | Documenti Microsoft'
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
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1653b0e903fd931d5df4b1dcce4dcbd99fbbae37
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Procedura: associare estensioni di codice gestito a documenti
  È possibile collegare un assembly di personalizzazione di un documento esistente di Microsoft Office Word o una cartella di lavoro di Microsoft Office Excel. Il documento o la cartella di lavoro può essere in qualsiasi formato di file supportato dai progetti di Microsoft Office e strumenti di sviluppo in Visual Studio. Per ulteriori informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Per associare una personalizzazione a un documento di Word o Excel, utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodo la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Poiché la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe è progettata per essere eseguito in un computer che non è installato Microsoft Office, è possibile utilizzare questo metodo nelle soluzioni che non sono direttamente correlate allo sviluppo di Microsoft Office (ad esempio, un'applicazione console o Windows Form).  
  
> [!NOTE]  
>  La personalizzazione non verrà caricato se il codice prevede che i controlli che non dispone del documento specificato.  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [come ricerca per categorie: allegare o scollegamento di un Assembly di VSTO da un documento di Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Per allegare estensioni di codice gestito a un documento  
  
1.  In un progetto Windows Form o un progetto che non richiede Microsoft Office, ad esempio un'applicazione console, aggiungere un riferimento di Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll e Microsoft.VisualStudio.Tools.Applications.Runtime.dll assembly.  
  
2.  Aggiungere il seguente **importazioni** o **utilizzando** istruzioni all'inizio del file di codice.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodo.  
  
     Nell'esempio di codice viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> rapporto di overload. Questo overload accetta il percorso completo del documento e una <xref:System.Uri> che specifica il percorso del manifesto di distribuzione per la personalizzazione che si desidera collegare al documento. Questo esempio si presuppone che un documento di Word denominato **WordDocument1.docx** sul desktop, e che il manifesto di distribuzione si trova in una cartella denominata **pubblica** che è anche sul desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera associare la personalizzazione. Il computer deve disporre di Visual Studio 2010 Tools per Office Runtime installato.  
  
## <a name="see-also"></a>Vedere anche  
 [La gestione dei documenti in un Server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  