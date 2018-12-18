---
title: Soluzioni Excel | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bfbb56e3e11cd260065adb8a25be4eccefdd40ad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="excel-solutions"></a>Soluzioni Excel
  Visual Studio fornisce modelli di progetto che è possibile usare per creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Excel. È possibile usare queste soluzioni per automatizzare Excel, estenderne le funzionalità e personalizzarne l'interfaccia utente. Per ulteriori informazioni sulle differenze tra personalizzazioni a livello di documento e componenti aggiuntivi VSTO, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Automazione di Excel](#automating)  
  
-   [Sviluppo di personalizzazioni a livello di documento per Excel](#doclevel).  
  
-   [Sviluppo di componenti aggiuntivi VSTO per Excel](#applevel).  
  
-   [Personalizzazione dell'interfaccia utente di Excel](#UI).  
  
##  <a name="automating"></a> Automazione di Excel  
 Il modello a oggetti di Excel espone diversi tipi che è possibile usare per automatizzare Excel. Ad esempio, è possibile creare grafici, formattare fogli di lavoro e impostare i valori degli intervalli e delle celle a livello di codice. Per altre informazioni, vedere [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 Quando si sviluppano soluzioni Excel in Visual Studio, si possono anche usare *elementi host* e *controlli host* nelle soluzioni. Si tratta di oggetti che estendono alcuni oggetti di uso comune nel modello a oggetti di Excel, ad esempio gli oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> e <xref:Microsoft.Office.Interop.Excel.Range> . Gli oggetti estesi si comportano come gli oggetti di Excel sui quali si basano, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti. Per altre informazioni, vedere [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Developing Document-Level Customizations for Excel  
 Una personalizzazione a livello di documento per Microsoft Office Excel è costituita da un assembly associato a una cartella di lavoro specifica. L'assembly in genere estende la cartella di lavoro personalizzando l'interfaccia utente e automatizzando Excel. Diversamente da un componente aggiuntivo VSTO a livello di applicazione, associato a Excel stesso, la funzionalità che si implementa in una personalizzazione è disponibile solo quando la cartella di lavoro associata è aperta in Excel.  
  
 Per creare un progetto relativo alla personalizzazione a livello di documento per Excel, usare i modelli di progetto relativi alla cartella di lavoro o al modello di Excel nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per altre informazioni sul funzionamento delle personalizzazioni a livello di documento, vedere [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="excel-customization-programming-model"></a>Modello di programmazione delle personalizzazioni di Excel  
 Quando si crea un progetto a livello di documento per Excel, in Visual Studio vengono generate diverse classi che costituiscono il fondamento della soluzione: `ThisWorkbook`, `Sheet1`, `Sheet2`e `Sheet3`. Queste classi rappresentano la cartella di lavoro e fogli di lavoro associati alla soluzione e forniscono un punto di partenza per la scrittura del codice.  
  
 Per altre informazioni su queste classi generate e su altre funzionalità che è possibile usare in un progetto a livello di documento, vedere [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Sviluppo di componenti aggiuntivi VSTO per Excel  
 Un componente aggiuntivo VSTO per Microsoft Office Excel è costituito da un assembly caricato da Excel. L'assembly in genere estende Excel personalizzando l'interfaccia utente e automatizzando Excel. A differenza di una personalizzazione a livello di documento, associata a una cartella di lavoro specifica, la funzionalità implementata in un componente aggiuntivo VSTO non è limitata a una singola cartella di lavoro.  
  
 Per creare un progetto di componente aggiuntivo VSTO per Excel, usare i modelli di progetto relativi alla cartella di lavoro o al modello di Excel nella finestra di dialogo **Nuovo progetto** di Visual Studio. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Per informazioni generali sul funzionamento dei componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [modalità per automatizzare PowerPoint da un componente aggiuntivo di Excel?](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### <a name="excel-add-in-programming-model"></a>Modello di programmazione dei componenti aggiuntivi di Excel  
 Quando si crea un progetto di componente aggiuntivo VSTO per Excel, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone anche il modello a oggetti di Excel nel componente aggiuntivo VSTO.  
  
 Per altre informazioni sulla classe `ThisAddIn` e su altre funzionalità di Visual Studio che è possibile usare in un componente aggiuntivo VSTO, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Customizing the User Interface of Excel  
 Sono disponibili diverse modalità per personalizzare l'interfaccia utente di Excel. Alcune opzioni sono disponibili per tutti i tipi di progetto e altre opzioni sono disponibili solo per i componenti aggiuntivi VSTO o le personalizzazioni a livello di documento.  
  
### <a name="options-for-all-project-types"></a>Opzioni per tutti i tipi di progetto  
 La tabella seguente elenca le opzioni di personalizzazione disponibili per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Personalizzare la barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere controlli Windows Form o controlli estesi di Excel a un foglio di lavoro della cartella di lavoro personalizzata per una personalizzazione a livello di documento, o in qualsiasi cartella di lavoro aperta per un componente aggiuntivo VSTO.|[Procedura: Aggiungere controlli Windows Forms a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Procedura: Aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opzioni per le personalizzazioni a livello di documento  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per le personalizzazioni a livello di documento.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Aggiunta di un riquadro delle azioni alla cartella di lavoro.|[Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)<br /><br /> [Procedura: Aggiungere un riquadro Azioni ai documenti Word o alle cartelle di lavoro Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Aggiungere a un foglio di lavoro controlli di intervallo esteso mappati ai nodi XML.|[Procedura: Aggiungere controlli XMLMappedRange a fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opzioni per i componenti aggiuntivi VSTO  
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per i componenti aggiuntivi VSTO.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Excel Object Model Overview](../vsto/excel-object-model-overview.md)|Fornisce una panoramica dei tipi principali forniti dal modello a oggetti di Excel.|  
|[Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)|Fornisce informazioni sugli oggetti estesi (forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) che è possibile usare nelle soluzioni Excel.|  
|[Globalizzazione e localizzazione di soluzioni di Excel](../vsto/globalization-and-localization-of-excel-solutions.md)|Contiene considerazioni speciali per le soluzioni Excel eseguite in computer che hanno impostazioni di Windows non in inglese.|  
|[Panoramica dei controlli Windows Forms nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Descrive come è possibile aggiungere controlli Windows Form ai fogli di lavoro di Excel.|  
|[Procedura dettagliata: creazione della prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Illustra come creare una personalizzazione di base a livello di documento per Excel.|  
|[Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Mostra come creare un componente aggiuntivo VSTO di base per Excel.|  
|[Procedura dettagliata: aggiunta di controlli a un foglio di lavoro in fase di esecuzione in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Illustra come aggiungere un pulsante di Windows Form, <xref:Microsoft.Office.Tools.Excel.NamedRange>e <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in fase di esecuzione con un componente aggiuntivo VSTO.|
|[Informazioni sulla creazione condivisa e sui componenti aggiuntivi](./understanding-coauthoring-and-addins.md)|Descrive le regolazioni che potrebbe essere necessario apportare alle soluzioni per supportare creazione condivisa.|  
|[Excel 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199011)|Fornisce collegamenti ad articoli e documentazione di riferimento sullo sviluppo di soluzioni Excel. Gli articoli non sono specifici per lo sviluppo di Office usando Visual Studio.|  
  
  