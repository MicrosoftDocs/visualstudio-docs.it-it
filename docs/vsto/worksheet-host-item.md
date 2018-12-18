---
title: Elemento Host foglio di lavoro | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c89fa79a73393afa2919554de790c307b2ea68b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="worksheet-host-item"></a>Elemento host Worksheet
  L'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> è un tipo che estende il tipo <xref:Microsoft.Office.Interop.Excel.Worksheet> dall'assembly di interoperabilità primario per Excel. L'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> offre tutte le stesse proprietà, gli stessi metodi ed eventi di un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> , ma espone anche eventi aggiuntivi e funge da contenitore per i controlli host e quelli Windows Form.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Nei progetti a livello di documento è possibile aggiungere elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> al progetto in fase di progettazione. Nei progetti di componente aggiuntivo VSTO è possibile generare elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione.  
  
## <a name="understanding-worksheet-host-items-in-document-level-projects"></a>Informazioni sugli elementi host Worksheet nei progetti a livello di documento  
 Quando si crea un progetto a livello di documento per Excel, Visual Studio automaticamente crea tre elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> nel progetto. I nomi predefiniti dei fogli di lavoro sono `Sheet1`, `Sheet2`e `Sheet3`. Se si crea un progetto in base a una cartella di lavoro esistente, il numero di elementi host dipende dal numero di fogli di lavoro nella cartella di lavoro.  
  
 Queste classi del foglio di lavoro offrono l'accesso ai membri dell'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> per eseguire attività di base nella personalizzazione, come ad esempio la modifica dei contenuti in un foglio di lavoro. È anche possibile usare queste classi per aggiungere controlli ai fogli di lavoro. Con la combinazione di set di controlli diversi e con la scrittura di codice, è possibile associare i controlli ai dati, raccogliere le informazioni relative all'utente e rispondere alle azioni utente. Per altre informazioni, vedere [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Le classi del foglio di lavoro offrono un punto di partenza per iniziare a scrivere codice nel progetto. Dal momento che la classe offre tutte le stesse proprietà, gli stessi metodi ed eventi dell'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nell'assembly di interoperabilità primario per Excel, è possibile usare anche queste classi per accedere al modello a oggetti di Excel. Per altre informazioni, vedere [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 Nei progetti a livello di documento è possibile aggiungere elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> aggiuntivi al progetto in fase di progettazione aggiungendo un nuovo foglio di lavoro nella finestra di progettazione.  
  
### <a name="renaming-worksheets"></a>Ridenominazione dei fogli di lavoro  
 In un progetto a livello di documento è possibile rinominare i fogli di lavoro nella finestra di progettazione di Visual Studio, ma in tal modo viene modificato solo il nome visualizzato del foglio di lavoro. Il nome a livello di codice rimane il nome predefinito del foglio di lavoro. Se si rinomina il foglio di lavoro nella finestra **Proprietà** , viene modificato solo il nome a livello di codice.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitazioni dell'elemento host Worksheet nei progetti a livello di documento  
 Non è possibile creare nuovi elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione in un progetto a livello di documento. Se si crea un nuovo foglio di lavoro Excel in fase di esecuzione, sarà di tipo <xref:Microsoft.Office.Interop.Excel.Worksheet>. Dal momento che non si tratta di un elemento host, non può contenere alcun controllo host o controllo Windows Form. Per ulteriori informazioni sulla creazione di documenti in fase di esecuzione, vedere [come: a livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understanding-worksheet-host-items-in-vsto-add-in-projects"></a>Informazioni sugli elementi host Worksheet in progetti di componente aggiuntivo VSTO  
 Nei progetti a livello di applicazione è possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione per qualsiasi foglio di lavoro in Excel. È possibile usare l'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> per aggiungere controlli al foglio di lavoro associato oppure per gestire eventi che non sono disponibili su oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> .  
  
 Per generare un <xref:Microsoft.Office.Tools.Excel.Worksheet> elemento host, utilizzare il metodo GetVstoObject. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento Host cartella di lavoro](../vsto/workbook-host-item.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  