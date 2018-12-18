---
title: Soluzioni Outlook | Documenti Microsoft
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
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c2ee35159e978150e7b63bacac127d5f7b8236c5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="outlook-solutions"></a>Soluzioni Outlook
  Visual Studio offre modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Outlook. È possibile usare i componenti aggiuntivi VSTO per automatizzare Outlook, estenderne le funzionalità o personalizzarne l'interfaccia utente. Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="creating-an-outlook-vsto-add-in-project"></a>Creazione di un nuovo progetto di componente aggiuntivo VSTO di Outlook  
 Creare progetti Outlook usando uno dei modelli di progetto **Componente aggiuntivo per Outlook** nella finestra di dialogo **Nuovo progetto** . Questo modello include i riferimenti agli assembly e i file di progetto necessari.  
  
 Per ulteriori informazioni su come creare un progetto di componente aggiuntivo VSTO, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per ulteriori informazioni sui modelli di progetto, vedere [panoramica dei modelli di progetto Office](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Modello di programmazione dei componenti aggiuntivi VSTO per Outlook  
 Quando si crea un progetto di componente aggiuntivo VSTO per Outlook, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone inoltre il modello a oggetti di Outlook nel componente aggiuntivo VSTO.  
  
 Per ulteriori informazioni sul `ThisAddIn` classe e altre funzionalità, è possibile utilizzare in un componente aggiuntivo VSTO, vedere [programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-outlook-by-using-the-outlook-object-model"></a>Automazione di Outlook mediante il modello a oggetti di Outlook  
 Il modello a oggetti di Outlook espone diversi tipi che è possibile usare per automatizzare Outlook. Questi tipi consentono di scrivere il codice per eseguire attività comuni:  
  
-   Creare e inviare messaggi di posta elettronica a livello di codice.  
  
-   Inviare nuove convocazioni riunione.  
  
-   Cercare elementi in cartelle di Outlook.  
  
 Per altre informazioni, vedere [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md).  
  
## <a name="customizing-the-user-interface-of-an-outlook-application"></a>Personalizzazione dell'interfaccia utente di un'applicazione di Outlook  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Aggiungere schede personalizzate alla barra multifunzione di un controllo di Outlook.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere gruppi personalizzati a una scheda predefinita in un controllo di Outlook.|[Procedura: Personalizzare una scheda predefinita](../vsto/how-to-customize-a-built-in-tab.md)|  
|Aggiungere un riquadro attività personalizzato da visualizzare in un controllo di Outlook|[Riquadri attività personalizzati](../vsto/custom-task-panes.md).|  
|Aggiungere un'area del modulo che estende o sostituisce moduli di Outlook esistenti.|[Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Outlook e altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)|Contiene una panoramica degli oggetti forniti dal modello a oggetti di Word.|  
|[Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)|Descrive gli strumenti disponibili in Visual Studio che semplificano la progettazione, lo sviluppo e il debug delle aree del modulo.|  
|[Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Mostra come creare un componente aggiuntivo VSTO per Microsoft Office Outlook.|  
|[Outlook 2010 nello sviluppo di applicazioni per Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Area di MSDN Library in cui è possibile trovare articoli e documentazione di riferimento sullo sviluppo di soluzioni Office (non specifiche per lo sviluppo di Office con Visual Studio).|  
  
  