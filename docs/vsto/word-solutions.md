---
title: Soluzioni di Word | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44cd5633d7cc03fb78c6508c24a117a0500fa142
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="word-solutions"></a>Soluzioni Word
  Visual Studio fornisce modelli di progetto che è possibile usare per creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Word. È possibile usare queste soluzioni per automatizzare Word, estenderne le funzionalità e personalizzarne l'interfaccia utente. Per ulteriori informazioni sulle differenze tra personalizzazioni a livello di documento e componenti aggiuntivi VSTO, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Automazione di Word](#automating).  
  
-   [Sviluppo di personalizzazioni a livello di documento per Word](#doclevel).  
  
-   [Sviluppo di componenti aggiuntivi VSTO per Word](#applevel).  
  
-   [Personalizzazione dell'interfaccia utente di Word](#UI).  
  
##  <a name="automating"></a> Automazione di Word  
 Il modello a oggetti di Word espone diversi tipi che è possibile usare per automatizzare Word. Ad esempio, è possibile creare tabelle, formattare documenti e impostare testo in intervalli e paragrafi a livello di codice. Per altre informazioni, vedere [Word Object Model Overview](../vsto/word-object-model-overview.md).  
  
 Quando si sviluppano soluzioni Word in Visual Studio, è anche possibile usare *elementi host* e *controlli host* nelle soluzioni. Si tratta di oggetti che estendono alcuni oggetti di uso comune nel modello a oggetti di Word, ad esempio gli oggetti <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl> . Gli oggetti estesi si comportano come gli oggetti di Word su cui sono basati, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti. Per altre informazioni, vedere [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Developing Document-Level Customizations for Word  
 Una personalizzazione a livello di documento per Microsoft Office Word è costituita da un assembly associato a un documento specifico. L'assembly in genere estende il documento personalizzando l'interfaccia utente e automatizzando Word. Diversamente da un componente aggiuntivo VSTO, associato a Word stesso, la funzionalità che si implementa in una personalizzazione è disponibile solo quando il documento associato è aperto in Word.  
  
 Per creare un progetto di personalizzazione a livello di documento per Word, usare il modello di progetto Documento di Word o Modello di Word nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per altre informazioni sul funzionamento delle personalizzazioni a livello di documento, vedere [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="word-customization-programming-model"></a>Modello di programmazione delle personalizzazioni di Word  
 Quando si crea un progetto a livello di documento per Word, Visual Studio genera una classe denominata `ThisDocument`, che costituisce il fondamento della soluzione. Questa classe rappresenta il documento associato alla soluzione e fornisce un punto di partenza per la scrittura del codice.  
  
 Per altre informazioni sulla classe `ThisDocument` e su altre funzionalità che è possibile usare in un progetto a livello di documento, vedere [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Sviluppo di componenti aggiuntivi VSTO per Word  
 Un componente aggiuntivo VSTO per Microsoft Office Word è costituito da un assembly caricato da Word. L'assembly in genere estende Word personalizzando l'interfaccia utente e automatizzando Word. A differenza di una personalizzazione a livello di documento, associata a un documento specifico, la funzionalità implementata in un componente aggiuntivo VSTO non è limitata a un singolo documento.  
  
 Per creare un progetto di componente aggiuntivo VSTO per Word, usare i modelli di progetto di componente aggiuntivo di Word nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per informazioni generali sul funzionamento dei componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="word-add-in-programming-model"></a>Modello di programmazione dei componenti aggiuntivi di Word  
 Quando si crea un progetto di componente aggiuntivo VSTO di Word, Visual Studio genera una classe denominata `ThisAddIn`, che costituisce il fondamento della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone anche il modello a oggetti di Word nel componente aggiuntivo VSTO.  
  
 Per altre informazioni sulla classe `ThisAddIn` e su altre funzionalità che è possibile usare in un componente aggiuntivo VSTO, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Customizing the User Interface of Word  
 Sono disponibili diverse modalità per personalizzare l'interfaccia utente di Word. Alcune opzioni sono disponibili per tutti i tipi di progetto e altre opzioni sono disponibili solo per i componenti aggiuntivi VSTO o le personalizzazioni a livello di documento.  
  
### <a name="options-for-all-project-types"></a>Opzioni per tutti i tipi di progetto  
 La tabella seguente elenca le opzioni di personalizzazione disponibili per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Personalizzare la barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere controlli Windows Form o controlli di Word estesi al documento personalizzato (per una personalizzazione a livello di documento) o a qualsiasi documento aperto (per un componente aggiuntivo VSTO).|[Procedura: Aggiungere controlli Windows Forms a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Procedura: Aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Procedura: Aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opzioni per le personalizzazioni a livello di documento  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per le personalizzazioni a livello di documento.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Aggiungere un riquadro Azioni al documento.|[Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)<br /><br /> [Procedura: Aggiungere un riquadro Azioni ai documenti Word o alle cartelle di lavoro Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Aggiungere controlli XMLNode e XMLNodes estesi all'area del documento.|[Procedura: Aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Procedura: Aggiungere controlli XMLNodes ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opzioni per i componenti aggiuntivi VSTO  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Word Object Model Overview](../vsto/word-object-model-overview.md)|Fornisce una panoramica dei tipi principali forniti dal modello a oggetti di Word.|  
|[Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)|Fornisce informazioni sugli oggetti estesi (forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) che è possibile usare nelle soluzioni Word.|  
|[Panoramica dei controlli Windows Forms nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Descrive come aggiungere controlli Windows Form ai documenti di Word.|  
|[Procedura dettagliata: creazione della prima personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Illustra come creare una personalizzazione di base a livello di documento per Word.|  
|[Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Illustra come creare un componente aggiuntivo VSTO di base per Word.|  
|[Procedura dettagliata: aggiunta di controlli a un documento in fase di esecuzione in un componente aggiuntivo VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Illustra come aggiungere un pulsante Windows Form e un oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a un documento in fase di esecuzione usando un componente aggiuntivo VSTO.|  
|[Word 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Fornisce collegamenti ad articoli e documentazione di riferimento sullo sviluppo di soluzioni Word (non specifici dello sviluppo per Office tramite Visual Studio).|  
  
  