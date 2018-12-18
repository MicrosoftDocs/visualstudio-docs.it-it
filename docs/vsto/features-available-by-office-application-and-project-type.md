---
title: "Funzionalità disponibili in base al tipo di progetto e applicazioni di Office | Documenti Microsoft"
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
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b79c7a913e8ce06b1d833f78aad9e8565d54aff2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="features-available-by-office-application-and-project-type"></a>Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office
  In Visual Studio sono disponibili numerosi tipi di modelli di progetto che supportano scenari aziendali diversi per le applicazioni di Microsoft Office, inclusi i tipi seguenti:  
  
-   Personalizzazioni a livello di documento.  
  
-   Componenti aggiuntivi VSTO.  
  
 Non tutte le applicazioni possono utilizzare ogni tipo di progetto. Ad esempio, i progetti a livello di documento sono disponibili solo per Microsoft Office Word e Microsoft Office Excel. Analogamente, alcune funzionalità sono disponibili solo per determinati tipi di progetti o applicazioni. Ad esempio, il riquadro azioni è disponibile solo nei progetti a livello di documento e le estensioni della barra multifunzione sono disponibili solo per alcune applicazioni. Per ulteriori informazioni sui diversi tipi di progetto, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Modelli di progetto di Office sono disponibili solo in alcune edizioni di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Tipi di progetto disponibili per applicazioni di Microsoft Office diverse  
 Nella tabella seguente sono indicate le applicazioni che è possibile utilizzare con ogni tipo di progetto.  
  
|Tipi di progetto|Applicazione Microsoft Office|  
|-------------------|----------------------------------|  
|Personalizzazioni a livello di documento|Excel<br /><br /> Word|  
|Componenti aggiuntivi VSTO|Excel<br /><br /> InfoPath (solo InfoPath 2013 e InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Progetto<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Funzionalità disponibili in diversi tipi di progetto  
 Nella tabella seguente sono indicati i tipi di progetto che forniscono ciascuna funzionalità.  
  
|Funzionalità|Tipi di progetto che forniscono la funzionalità|Ulteriori informazioni|  
|-------------|--------------------------------------------|---------------------|  
|Riquadro azioni.|Progetti a livello di documento.|[Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)|  
|Distribuzione ClickOnce.|Progetti a livello di documento e VS.|[Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)|  
|Riquadri attività personalizzati.|Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-Outlook<br />-PowerPoint<br />-Word|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
|Parti XML personalizzate.|Progetti a livello di documento.<br /><br /> Progetti di livello applicazione per le applicazioni seguenti:<br /><br /> -Excel<br />-PowerPoint<br />-Word|[Panoramica sulle Web part XML personalizzate](../vsto/custom-xml-parts-overview.md)|  
|Cache dei dati.|Progetti a livello di documento.|[Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)|  
|Esporre un oggetto in un componente aggiuntivo VSTO ad altre soluzioni Microsoft Office.|Progetti di componente aggiuntivo VSTO.|[Chiamata di codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|I controlli host seguenti:<br /><br /> -Grafico<br />-ListObject<br />-NamedRange<br />-Controlli contenuto<br />-Segnalibro|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per Word ed Excel.|[Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)|  
|I controlli host seguenti:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Progetti a livello di documento.|[Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)|  
|Distribuzione di più progetti.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: Distribuzione di più soluzioni Office in un singolo programma di installazione ClickOnce](http://msdn.microsoft.com/en-us/051223c0-4082-4799-b78b-a4763a9def55)|  
|Aree di modulo di Outlook.|Progetti di componente aggiuntivo VSTO per Outlook.|[Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)|  
|Azioni di post-distribuzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: Copia di un documento per i Computer dell'utente finale dopo un'installazione di ClickOnce](http://msdn.microsoft.com/en-us/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Personalizzazioni della barra multifunzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-Outlook<br />-PowerPoint<br />-Progetto<br />-Visio<br />-Word|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
|Programma di creazione documenti visivi.|Progetti a livello di documento.|[Progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida introduttiva &#40; sviluppo per Office in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Cenni preliminari sullo sviluppo di soluzioni Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  