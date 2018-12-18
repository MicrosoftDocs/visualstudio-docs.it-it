---
title: Creazione di definizioni di sito per SharePoint | Documenti Microsoft
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d29ab819dfc7efd04d27652ab3d711c89045847c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="creating-site-definitions-for-sharepoint"></a>Creazione di definizioni di sito per SharePoint
  Il progetto di definizione del sito di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di creare un *definizione sito*, che funge da base per un nuovo sito di SharePoint. Queste definizioni determinano non solo l'aspetto e il comportamento del sito di SharePoint, ma anche il contenuto predefinito e funzionalità. Nella definizione è possibile inserire elenchi preconfigurati, tipi di contenuto, ricevitori di eventi, immagini e altri elementi. In SharePoint sono incluse alcune definizioni di sito come BLOG, ad esempio. Quando si crea un sito in base alla definizione di sito BLOG, il sito contiene gli elenchi, Web part e altri elementi richiesti da un sito blog.  
  
 Per ulteriori informazioni sulle definizioni di sito, vedere [modelli di sito e le definizioni di](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Progetti di definizione sito  
 Progetti di definizione sito [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] forniscono solo i file di base necessarie per un sito di SharePoint, non forniscono le funzionalità predefinite. È necessario aggiungere i file e il contenuto per fornire la funzionalità che si desidera. È possibile compilare il sito manualmente, creando e aggiungendo i file necessari.  
  
## <a name="feature-stapling"></a>Associazione delle funzionalità  
 Un vantaggio della creazione di definizioni di sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] è l'utilizzo automatico *associazione delle funzionalità*. L'associazione delle funzionalità collega una funzionalità a una definizione di sito anziché incorporare le funzionalità nella definizione del sito stesso. Questa operazione consente di aggiungere la funzionalità a qualsiasi sito creato tramite la definizione del sito senza modificare la definizione di sito originale. Per ulteriori informazioni, vedere [associazione delle funzionalità](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Componenti del progetto di definizione del sito  
 Quando si crea una soluzione di definizione del sito, i seguenti file predefiniti vengono aggiunti al relativo **SiteDefinition** nodo.  
  
|Nome file|Descrizione|  
|---------------|-----------------|  
|default.aspx|Pagina home ASPX predefinita per il nuovo sito di SharePoint.|  
|Onet.Xml|Specifica la configurazione del nuovo sito, i componenti del modello di definizione del sito e il comportamento predefinito. Queste impostazioni possono includere attributi, ad esempio i tipi di contenuto che sono abilitati, le visualizzazioni elenco predefinite, il file di modello di documento e le Web part incluse nel sito. Per impostazione predefinita, il `Modules` sezione sono elencati i file da aggiungere al sito di SharePoint e modalità di configurazione.|  
|webtemp_*SiteDefinitionName*. Xml|Specifica le configurazioni di definizione del sito che viene visualizzato nel **selezione modello** sezione la **nuovo sito di SharePoint** pagina.|  
  
 Per impostazione predefinita, tutte le definizioni di sito vengono archiviate nel *unità:*cartella \Programmi\File comuni\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates. Ogni definizione di sito è una sottocartella.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura dettagliata: creare un progetto di definizione di sito di base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Illustra la procedura dettagliata tramite la creazione di un progetto di definizione di sito di base in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Procedura: creare una definizione di sito personalizzato e una configurazione](http://go.microsoft.com/fwlink/?LinkId=183309)|Viene descritto come creare una definizione di sito personalizzato in SharePoint copiando una definizione di sito esistente e quindi modificando tale copia.|  
|[Webtemp](http://go.microsoft.com/fwlink/?LinkId=183310)|Descrive il file originale che specifica le definizioni di sito disponibile nel **selezione modello** sezione la **nuovo sito di SharePoint** pagina.|  
|[Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Viene descritto come preparare le soluzioni di SharePoint per l'utilizzo generale.|  
|[Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Viene descritto come creare parti di una pagina di SharePoint che gli utenti possono modificare.|  
|[Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Viene descritto come creare controlli riutilizzabili che vengono eseguiti nelle pagine di applicazione e Web part.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Viene descritto come utilizzare la finestra di progettazione viene visualizzata quando si apre una pagina Web nel progetto.|  
|[Cenni preliminari sulle pagine Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Vengono fornite informazioni generali sulla struttura di [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] delle pagine Web, la modalità di elaborazione delle pagine da [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]e come [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] markup conforme agli standard XHTML visualizzato nelle pagine.|  
|[Sintassi di pagine Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Vengono descritti gli elementi di markup che costituiscono una pagina ASP.NET.|  
|[Pagine Web ASP.NET di programmazione](http://go.microsoft.com/fwlink/?LinkId=178728)|Vengono fornite informazioni su come creare gestori eventi in [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine e le modalità di utilizzo di script client.|  
|[Programmazione di Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Viene descritto come utilizzare il modello a oggetti gestito che viene fornito in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  