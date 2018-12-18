---
title: Guida introduttiva di programmazione dei componenti aggiuntivi VSTO | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f395ce7fb85d71ed6e8c3f7dfb10726907832873
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="getting-started-programming-vsto-add-ins"></a>Getting Started Programming VSTO Add-ins
  È possibile usare componenti aggiuntivi VSTO per automatizzare le applicazioni di Microsoft Office, estendere le funzionalità dell'applicazione e personalizzare l'interfaccia utente dell'applicazione. Per informazioni sul confronto tra i componenti aggiuntivi VSTO e altri tipi di soluzioni Office create tramite Visual Studio, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="creating-vsto-add-in-projects"></a>Creazione di progetti di componente aggiuntivo VSTO  
 Creare progetti di componente aggiuntivo VSTO usando uno dei modelli di progetto del componente aggiuntivo VSTO nella finestra di **nuovo progetto** la finestra di dialogo. Questi modelli includono riferimenti dell'assembly e file di progetto necessari. Visual Studio offre modelli di progetto di componente aggiuntivo VSTO per la maggior parte delle applicazioni di Office.  
  
 Per ulteriori informazioni su come creare un progetto di componente aggiuntivo VSTO, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per ulteriori informazioni sui modelli di progetto, vedere [panoramica dei modelli di progetto Office](../vsto/office-project-templates-overview.md).  
  
## <a name="developing-vsto-add-in-projects"></a>Sviluppo di progetti di componente aggiuntivo VSTO  
 Quando si crea un progetto di componente aggiuntivo VSTO, Visual Studio crea automaticamente un ThisAddIn. vb (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) o file di codice ThisAddIn.cs (in c#). Questo file contiene il `ThisAddIn` (classe), che fornisce le basi per il componente aggiuntivo VSTO. È possibile usare i membri di questa classe per eseguire il codice quando il componente aggiuntivo VSTO viene caricato o scaricato, per accedere al modello a oggetti dell'applicazione host e per estendere le funzionalità dell'applicazione. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-applications-by-using-the-object-models"></a>Automazione di applicazioni utilizzando i modelli a oggetti  
 I modelli a oggetti delle applicazioni di Microsoft Office espongono molti tipi per i quali è possibile eseguire la programmazione in un componente aggiuntivo VSTO. È possibile utilizzare questi tipi per automatizzare l'applicazione. Ad esempio, a livello di programmazione, è possibile creare e inviare un messaggio di posta elettronica in Outlook o è possibile aprire un documento e aggiungere contenuto in Word. Per ulteriori informazioni su come accedere al modello a oggetti dell'applicazione host nel codice, vedere [programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Per altre informazioni sui modelli a oggetti di applicazioni specifiche di Microsoft Office, vedere gli argomenti seguenti:  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [Soluzioni InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluzioni Project](../vsto/project-solutions.md)  
  
-   [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customizing-the-user-interface-of-applications"></a>Personalizzazione dell'interfaccia utente delle applicazioni  
 Esistono diversi modi per personalizzare l'interfaccia utente dell'applicazione host mediante un componente aggiuntivo VSTO:  
  
-   Per Excel e Word, è possibile aggiungere controlli gestiti ai documenti. Per altre informazioni, vedere [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Se l'applicazione la supporta, è possibile personalizzare la barra multifunzione. Per ulteriori informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
-   Se l'applicazione lo supporta, è possibile creare un riquadro attività personalizzato. Per ulteriori informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
-   Per Outlook, è possibile creare un'area del modulo personalizzato. Per altre informazioni, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
-   Per tutte le applicazioni di Microsoft Office, è possibile visualizzare Windows Form nel componente aggiuntivo VSTO.  
  
 Per ulteriori informazioni su come personalizzare le applicazioni dell'interfaccia utente di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per informazioni su come creare componenti aggiuntivi VSTO, vedere le procedure dettagliate seguenti:  
  
-   [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Queste procedure dettagliate presentano gli strumenti di sviluppo per Office disponibili in Visual Studio e il modello di programmazione per i componenti aggiuntivi VSTO.  
  
 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Office, vedere [attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Guida introduttiva &#40; sviluppo per Office in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  