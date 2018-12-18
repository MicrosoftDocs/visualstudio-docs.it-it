---
title: Sviluppo di soluzioni Office | Documenti Microsoft
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
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bb3727d95fab03d2485c26f5858e0dbea7fe7543
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="developing-office-solutions"></a>Sviluppo di soluzioni Office
  Dopo aver progettato un progetto usando gli strumenti di sviluppo di Office in Visual Studio e configurato i file di progetto, è possibile iniziare a concentrarsi sull'implementazione del codice e dell'interfaccia utente personalizzata.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="office-solutions-programming-model"></a>Modello di programmazione delle soluzioni Office  
 Il modello a oggetti Office espone una serie di oggetti programmabili. Ogni volta che è possibile programmare soluzioni Office usando codice gestito, è necessario scrivere codice che usa tipi negli assembly di interoperabilità primari di Office. Nelle soluzioni create mediante i modelli di progetto di Office in Visual Studio, è inoltre possibile scrivere il codice direttamente per le classi generate del progetto. Per altre informazioni, vedere [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="programming-different-types-of-office-solutions"></a>Programmazione di tipi diversi di soluzioni Office  
 Il tipo di soluzione che si sta creando determina le funzionalità che è possibile usare nel progetto. Ad esempio, è possibile aggiungere controlli Windows Form e controlli estesi di Office (denominato *controlli host*) alle personalizzazioni a livello di documento trascinando gli elementi dalla **casella degli strumenti** in Visual Studio in fase di progettazione. Tuttavia, se si sviluppa un componente aggiuntivo VSTO, è possibile aggiungere questi tipi di controlli solo a documenti in fase di esecuzione, mediante la scrittura di codice.  
  
 Per altre informazioni sulle funzionalità specifiche di tipi diversi di soluzioni, vedere gli argomenti seguenti:  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
-   [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
 Per informazioni generali utili per pianificare le procedure e soluzioni Office per creare progetti, vedere [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)|Vengono descritti diversi aspetti della scrittura del codice nelle soluzioni Office.|  
|[Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)|Offre una panoramica del modello di programmazione dei componenti aggiuntivi VSTO e delle attività di programmazione correlate.|  
|[Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)|Viene fornita una panoramica del modello di programmazione delle personalizzazioni a livello di documento e delle attività di programmazione correlate.|  
|[Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)|Descrive i diversi modi in cui è possibile personalizzare l'interfaccia utente delle applicazioni di Office mediante componenti aggiuntivi VSTO e personalizzazioni a livello di documento.|  
|[Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)|Vengono descritti i diversi modi in cui è possibile usare i dati nelle soluzioni Office come, ad esempio, l'associazione dei dati ai controlli e la memorizzazione nella cache di dati in personalizzazioni a livello di documento.|  
|[Come il salvataggio automatico influisce sulle soluzioni Office](./how-autosave-impacts-office-solutions.md)|Descrive le regolazioni che potrebbe essere necessario apportare alle soluzioni Office quando è abilitato.|
|[Risoluzione dei problemi relativi alle soluzioni Office](../vsto/troubleshooting-office-solutions.md)|Vengono forniti suggerimenti per la risoluzione dei problemi comuni che possono verificarsi durante la creazione di soluzioni Office.|  
|[Supporto del threading in Office](../vsto/threading-support-in-office.md)|Viene fornita una panoramica dell'utilizzo di più thread nelle soluzioni Office.|  
|[Accessibilità nei progetti di Office](../vsto/accessibility-in-office-projects.md)|Vengono descritte le funzionalità di accessibilità disponibili nelle soluzioni Office.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare e modificare le proprietà personalizzate dei documenti](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Procedura: leggere e scrivere nelle proprietà dei documenti](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Procedura: l'interfaccia utente multilingue di Office di destinazione](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Procedura dettagliata: Creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procedura dettagliata: Creazione del componente aggiuntivo VSTO prima per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Procedura dettagliata: Creazione del componente aggiuntivo VSTO prima per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Procedura dettagliata: Creazione del componente aggiuntivo VSTO prima per il progetto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Procedura dettagliata: Creazione del componente aggiuntivo VSTO prima per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Procedura dettagliata: creazione della prima personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  