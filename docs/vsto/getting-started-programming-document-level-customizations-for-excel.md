---
title: Guida introduttiva di programmazione delle personalizzazioni a livello di documento per Excel | Documenti Microsoft
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
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fdf4afeb260d94b9e121628163c760244ac5f6e1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Guida introduttiva alla programmazione di personalizzazioni a livello di documento per Excel
  Se per iniziare la creazione di personalizzazioni a livello di documento per Microsoft Office Excel tramite Visual Studio, ecco cosa è necessario conoscere.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>Informazioni sulle personalizzazioni a livello di documento per Excel  
 Una personalizzazione a livello di documento per Excel è basata su una singola cartella di lavoro. Per iniziare a utilizzare la personalizzazione, l'utente finale apre la cartella di lavoro o crea la cartella di lavoro da un modello di Excel. Gli eventi nella cartella di lavoro, ad esempio digitando le celle o facendo clic di pulsanti e voci di menu, possono chiamare i metodi di gestione degli eventi nell'assembly. Quando la cartella di lavoro viene chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Excel, solo nel documento che conteneva.  
  
 Per ulteriori informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-excel"></a>Creazione di progetti a livello di documento per Excel  
 Per creare una personalizzazione a livello di documento per Excel, utilizzare il modello di progetto di cartella di lavoro di Excel o modello di Excel nel **nuovo progetto** la finestra di dialogo. Questi modelli includono riferimenti dell'assembly e file di progetto necessari.  
  
 Per ulteriori informazioni su come creare un progetto a livello di documento per Excel, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per ulteriori informazioni sui modelli di progetto, vedere [panoramica dei modelli di progetto Office](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>Cartelle di lavoro di Excel programmazione tramite gli elementi Host e controlli Host  
 *Elementi host* e *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento create mediante Visual Studio.  
  
 Gli elementi host forniscono un punto di ingresso per il codice e può anche fungono da contenitori per i controlli host e controlli Windows Form. Nei progetti a livello di documento per Excel, questi elementi host sono rappresentati di `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3` classi.  
  
 Controlli host sono basati sugli oggetti nativi di Excel, ad esempio gli oggetti elenco e gli intervalli. Controlli host offrono funzionalità simili per gli oggetti nativi di Excel, ma dispongono anche di funzionalità di data binding, supporto della finestra di progettazione e nuovi eventi. Vengono visualizzate come oggetti di prima classe nel codice del progetto in IntelliSense, che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza dover passare il modello a oggetti Excel.  
  
 Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>Personalizzazione dell'interfaccia utente di Excel  
 La maggior parte delle soluzioni di Microsoft Office modificare l'interfaccia utente (UI) dell'applicazione di Office allo scopo di consentire agli utenti di interagire con la soluzione. Esistono molti modi in cui è possibile modificare l'interfaccia utente di Excel usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione oppure è possibile visualizzare un riquadro azioni. Per ulteriori informazioni, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
 È anche possibile aprire la cartella di lavoro associata direttamente al progetto in Visual Studio. Quando la cartella di lavoro è aperta in Visual Studio, è possibile modificare la cartella di lavoro tramite l'interfaccia utente di Excel. È anche possibile utilizzare la cartella di lavoro come un'area di progettazione, che consente di trascinare i controlli in fogli di lavoro. Per ulteriori informazioni, vedere [progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="using-data-binding"></a>Utilizzo dell'associazione dati  
 I controlli host sono anche nell'elenco di controlli che è possibile trascinare il **origini dati** finestra. Aggiunta di controlli host in questo modo automaticamente li associa l'origine dati configurata mediante la finestra. Senza scrivere alcun codice, è possibile visualizzare i dati dal database, servizi web e oggetti business. Per ulteriori informazioni, vedere [associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per informazioni su come creare una personalizzazione a livello di documento per Excel, vedere [procedura dettagliata: creazione del primo a livello di documento personalizzazione per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Questa procedura dettagliata illustra gli strumenti di sviluppo per Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Excel.  
  
 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Excel, vedere [attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Soluzioni Excel](../vsto/excel-solutions.md)   
 [Procedura dettagliata: Creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [Panoramica del modello oggetto di Excel](../vsto/excel-object-model-overview.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
  
  