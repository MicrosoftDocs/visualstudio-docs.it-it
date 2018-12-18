---
title: Accessibilità nei progetti di Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8416e3fb5d5f46709870ffc3c7247c564bc845ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="accessibility-in-office-projects"></a>Accessibilità nei progetti di Office
  Microsoft Visual Studio e Microsoft Office includono molte funzionalità di accessibilità che consentono di creare soluzioni personalizzate che soddisfano i requisiti di accessibilità standard. Microsoft pubblica linee guida per l'accesso facilitato sul Web. Per informazioni dettagliate, vedere il [sito Web di accessibilità](http://go.microsoft.com/fwlink/?LinkID=37113).  

 Nella maggior parte dei casi, i progetti di Office in Visual Studio soddisfano accessibilità standard oppure espone le proprietà che è possibile impostare per rendere accessibili le soluzioni. Esistono tuttavia alcune funzionalità che non dispongono di accessibilità.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Accessibilità in fase di progettazione  

### <a name="using-shortcut-keys-in-document-level-projects"></a>Tasti di scelta rapida in progetti a livello di documento  
 Quando un documento di Microsoft Office Word o una cartella di lavoro di Microsoft Office Excel è aperto in Visual Studio, solo un'applicazione in un momento riceve i comandi dei tasti di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile apportare Word o Excel riceverli quando il documento ha lo stato attivo selezionando **schema della tastiera dinamico** sul **impostazioni della tastiera** pagina del **opzioni** la finestra di dialogo. Per ulteriori informazioni, vedere [tastiera di Microsoft Office Word, impostazioni tastiera Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) e [tastiera di Microsoft Office Excel, impostazioni tastiera Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="displaying-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Visualizzazione di tasti di scelta rapida per la barra multifunzione nei progetti a livello di documento  
 Quando un documento di Word o una cartella di lavoro di Excel è aperto in Visual Studio, è possibile premere il tasto Alt per visualizzare i tasti di scelta rapida per le schede e controlli della barra multifunzione. Per visualizzare i tasti di scelta rapida, mentre il documento o la cartella di lavoro è aperto nella finestra di progettazione, eseguire la procedura seguente.  

##### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Per visualizzare i tasti di scelta rapida per le schede della barra multifunzione e i controlli nella finestra di progettazione  

1.  In Visual Studio, sul **strumenti** menu, fare clic su **opzioni**.  

2.  Espandere il **gli strumenti di Office** nodo e selezionare **tastiera di Microsoft Office Excel** o **tastiera Microsoft Office Word**, a seconda dei casi.  

3.  Selezionare **schema della tastiera dinamico**.  

     Viene visualizzato un messaggio indicante che è necessario riavviare Visual Studio per la modifica diventi effettiva.  

4.  Fare clic su **OK**.  

5.  Riavviare Visual Studio e riaprire il progetto.  

6.  Aprire la finestra di progettazione per il progetto di documento o cartella di lavoro.  

7.  Premere F6 per visualizzare i tasti di scelta rapida per la barra multifunzione.  

## <a name="accessibility-at-run-time"></a>Accessibilità in fase di esecuzione  

### <a name="windows-forms-controls-on-office-documents"></a>Controlli Windows Form nei documenti di Office  
 Controlli Windows Form espongono proprietà di accessibilità per fornire informazioni sul controllo agli strumenti di accessibilità, ad esempio gli screen reader. È possibile sfruttare queste proprietà quando si trovano i controlli in un documento di Office in una personalizzazione a livello di documento. Per ulteriori informazioni, vedere [fornendo informazioni sull'accessibilità per i controlli in un Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 Tuttavia, esistono alcune limitazioni di accessibilità in fase di esecuzione quando sono ospitati i controlli Windows Form in una cartella di lavoro di Excel o di un documento di Word:  

-   È Impossibile scheda da un controllo a un altro.  

-   Controlli in un documento sono disabilitati quando si modifica l'impostazione dello zoom del documento in un valore diverso da 100%.  

 Per informazioni sulle limitazioni dei controlli Windows Form nei documenti, vedere [limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Riquadri azioni e riquadri attività personalizzati  
 Quando un riquadro azioni o un riquadro attività personalizzato è attivo, accedere ai controlli allo stesso modo, è possibile accedere a controlli in un'applicazione Windows Form. Per spostare il cursore tra il riquadro azioni e il documento, è possibile premere **F6**.  

 Per ulteriori informazioni sui riquadri azioni e riquadri attività personalizzati, vedere [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md) e [riquadri attività personalizzati](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Modalità di visualizzazione  
 Visual Studio presenta le seguenti limitazioni relative alle modalità di visualizzazione:  

-   Controlli in un documento di Word o un foglio di lavoro di Excel sono disabilitati quando si modifica l'impostazione dello zoom del documento in un valore diverso da 100%.  

-   Il **nuovo progetto** la finestra di dialogo controlli vengono visualizzati correttamente se un utente modifica le opzioni di accessibilità del computer per **Usa Contrasto elevato**.  

 È possibile utilizzare lente di ingrandimento per superare queste limitazioni. Lente di ingrandimento è un'utilità di Windows che consente di creare una finestra separata che consente di visualizzare un'area ingrandita della schermata.  

## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Accessibilità per persone affette da disabilità](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Accessibility Features of Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio) (Funzionalità di accessibilità di Visual Studio)  
