---
title: Elemento Host documento | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71a4f34e5ecc814ac732adddbfe0a82b05b84198
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="document-host-item"></a>Elemento host Document
  L'elemento host <xref:Microsoft.Office.Tools.Word.Document> è un tipo che estende il tipo <xref:Microsoft.Office.Interop.Word.Document> dall'assembly di interoperabilità primario per Word. L'elemento host <xref:Microsoft.Office.Tools.Word.Document> offre tutte le stesse proprietà, gli stessi metodi ed eventi di un oggetto <xref:Microsoft.Office.Interop.Word.Document> , ma espone anche eventi aggiuntivi e funge da contenitore per i controlli host e quelli Windows Form.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Nei progetti a livello di documento è presente un elemento host predefinito <xref:Microsoft.Office.Tools.Word.Document> che rappresenta il documento nel progetto. Nei progetti di componente aggiuntivo VSTO è possibile generare elementi host <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione.  
  
## <a name="understanding-the-document-host-item-in-document-level-projects"></a>Informazioni sull'elemento host Document nei progetti a livello di documento  
 Per accedere al documento nel progetto, usare la classe `ThisDocument` . Quando si crea un progetto a livello di documento, Visual Studio genera la classe `ThisDocument` che funge da collegamento per la comunicazione tra Word e il codice di personalizzazione. La classe `ThisDocument` consente l'accesso ai membri dell'elemento host <xref:Microsoft.Office.Tools.Word.Document> per eseguire attività di base nella personalizzazione, ad esempio eseguire codice quando il documento è aperto o chiuso. La classe può essere usata anche per aggiungere controlli al documento. Con la combinazione di set di controlli diversi e con la scrittura di codice, è possibile associare i controlli ai dati, raccogliere le informazioni relative all'utente e rispondere alle azioni utente. Per altre informazioni, vedere [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 La classe `ThisDocument` offre un punto di partenza per iniziare a scrivere codice nel progetto. Dal momento che la classe offre tutte le stesse proprietà, gli stessi metodi ed eventi dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> nell'assembly di interoperabilità primario per Word, è possibile usare anche `ThisDocument` per accedere al modello a oggetti di Word. Per altre informazioni, vedere [Word Object Model Overview](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Limitazioni dell'elemento host Document nei progetti a livello di documento  
 Un progetto a livello di documento può contenere solo un elemento host <xref:Microsoft.Office.Tools.Word.Document> (ossia, la classe `ThisDocument` ). Non è possibile aggiungere nuovi elementi host <xref:Microsoft.Office.Tools.Word.Document> al progetto in fase di progettazione, né creare nuovi elementi host <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione da una personalizzazione a livello di documento.  
  
 Se si crea un nuovo documento Word in fase di esecuzione, sarà di tipo <xref:Microsoft.Office.Interop.Word.Document>. Dal momento che non si tratta di un elemento host, non può contenere alcun controllo host o controllo Windows Form. Per ulteriori informazioni sulla creazione di documenti in fase di esecuzione, vedere [procedura: creare a livello di codice nuovi documenti](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understanding-document-host-items-in-application-level-projects"></a>Informazioni sugli elementi host Document nei progetti a livello di applicazione  
 Nei progetti di componente aggiuntivo VSTO è possibile generare un elemento host <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione per qualsiasi documento aperto in Word. È possibile usare l'elemento host <xref:Microsoft.Office.Tools.Word.Document> per aggiungere controlli al documento associato oppure per gestire eventi che non sono disponibili in oggetti <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Per generare un <xref:Microsoft.Office.Tools.Word.Document> elemento host, utilizzare il metodo GetVstoObject. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  