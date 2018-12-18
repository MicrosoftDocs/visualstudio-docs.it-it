---
title: Automazione di Word utilizzando oggetti estesi | Documenti Microsoft
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
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b3073f5f80e805f4c55e6924ada1be9a2ba139f6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="automating-word-by-using-extended-objects"></a>Automazione di Word usando oggetti estesi
  Quando si sviluppano soluzioni Word in Visual Studio, è possibile usare *elementi host* e *controlli host*nelle soluzioni. Si tratta di oggetti che estendono determinati oggetti usati comunemente nel modello a oggetti di Word (cioè, il modello a oggetti esposto dall'assembly di interoperabilità primario per Word), come ad esempio gli oggetti <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl> . Gli oggetti estesi si comportano come gli oggetti di Word su cui sono basati, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Gli elementi e i controlli host sono disponibili nelle personalizzazioni a livello di documento e dei componenti aggiuntivi VSTO, sebbene il contenuto in cui possono essere usati è diverso per ogni tipo di soluzione. Per altre informazioni, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Elemento host Document  
 I progetti Word consentono l'accesso all'elemento host <xref:Microsoft.Office.Tools.Word.Document> . L'elemento host <xref:Microsoft.Office.Tools.Word.Document> viene usato come contenitore per altri controlli, inclusi i controlli host e quelli Windows Form, e gestisce informazioni relative ai controlli della relativa area. L'elemento host <xref:Microsoft.Office.Tools.Word.Document> fornisce anche la maggior parte dei membri della classe <xref:Microsoft.Office.Interop.Word.Document> , ovvero la classe corrispondente nel modello a oggetti di Word.  
  
 Per altre informazioni, vedere [Document Host Item](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>Controlli host di Word  
 Vi sono vari controlli host per Word che consentono di creare, organizzare e automatizzare i documenti. La maggior parte delle funzionalità offerte include l'importazione, la presentazione e la protezione dei dati. Si tratta di controlli host che forniscono funzionalità di data binding ed eventi che non sono disponibili nelle rispettive controparti del modello a oggetti di Word nativo.  
  
 Nei progetti a livello di documento è possibile aggiungere al documento qualsiasi controllo host in fase di progettazione oppure controlli contenuto e controlli segnalibro in fase di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere controlli contenuto e segnalibro a qualsiasi documento aperto in fase di esecuzione.  
  
 Per altre informazioni sui controlli host da poter usare in progetti Word, vedere i seguenti argomenti:  
  
-   [Controlli del contenuto](../vsto/content-controls.md)  
  
-   [Controllo Bookmark](../vsto/bookmark-control.md)  
  
-   [Controllo XMLNode](../vsto/xmlnode-control.md)  
  
-   [Controllo XMLNodes](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Procedura: ridimensionare i controlli segnalibro](../vsto/how-to-resize-bookmark-controls.md)   
 [Procedura dettagliata: Creazione di un modello mediante controlli contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Procedura dettagliata: Associazione di controlli contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Procedura dettagliata: Creazione di menu di scelta rapida per segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  