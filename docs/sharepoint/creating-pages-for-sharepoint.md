---
title: Creazione di pagine per SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f484c0501cbeede5600a4831d3d872ac81b3b5c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-pages-for-sharepoint"></a>Creazione di pagine per SharePoint
  È possibile creare le pagine dell'applicazione, pagine del sito, pagine master e layout di pagina per un sito di SharePoint.  
  
 È possibile creare le pagine dell'applicazione utilizzando un modello in Visual Studio. Creare pagine del sito, pagine master e layout di pagina utilizzando SharePoint Designer. Quindi, è possibile importare queste pagine in Visual Studio per utilizzarli in un progetto SharePoint.  
  
 È inoltre possibile modificare l'aspetto e il comportamento delle pagine tramite fogli di stile CSS, ECMAScript e temi.  
  
## <a name="types-of-sharepoint-pages"></a>Tipi di pagine di SharePoint  
 Nella tabella seguente vengono descritti i quattro tipi principali di pagine che contiene un sito di SharePoint.  
  
|Tipo di pagina|Descrizione|  
|---------------|-----------------|  
|Pagine dell'applicazione|Se si desidera che la pagina contenga codice personalizzato o si desidera che la pagina per essere condivisi tra più siti, creare una pagina dell'applicazione. In caso contrario, una pagina del sito potrebbe essere la scelta migliore.|  
|Pagine del sito|Creare una pagina del sito se si desidera eseguire una delle seguenti operazioni:<br /><br /> -Aggiungere la pagina a una raccolta di SharePoint.<br />-Abilitare la pagina per includere funzionalità quali la Web part dinamiche e aree Web Part.<br />-Consentire agli utenti di personalizzare la pagina utilizzando SharePoint Designer.<br /><br /> Non creare una pagina del sito se si desidera che la pagina contenga codice personalizzato. Sebbene sia possibile aggiungere codice personalizzato a una pagina del sito, il codice si interrompe quando l'utente Personalizza la pagina utilizzando SharePoint Designer.|  
|Pagine master|Creare una pagina master se si desidera definire una struttura comune per le pagine del sito e le pagine dell'applicazione.|  
|Layout di pagina|Layout di pagina sono specifici di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] e consentono di definire ulteriormente una struttura comune per le pagine di applicazione del sito.|  
  
 Per una panoramica di ogni tipo di pagina, vedere [blocco predefinito: pagine e l'interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095), e [pagine Master e layout di pagina](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="creating-application-pages"></a>Creazione di pagine applicazione  
 È possibile creare le pagine dell'applicazione in Visual Studio aggiungendo un **pagina applicazione** elemento a un progetto SharePoint. È possibile aggiungere controlli alla pagina e quindi gestire gli eventi di controllo aggiungendo il codice.  
  
 È possibile impostare i punti di interruzione nel file di codice della pagina, avviare il debugger e testare la pagina in un sito di SharePoint locale senza eseguire ulteriori passaggi di configurazione. Per ulteriori informazioni, vedere [la creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>Creazione di pagine del sito, pagine Master e layout di pagina  
 È possibile creare pagine del sito, pagine master e layout di pagina utilizzando SharePoint Designer. Quindi, è possibile importare queste pagine in Visual Studio. Se si desidera sfruttare la distribuzione o la funzionalità di controllo di origine che sono disponibili in Visual Studio, importare le pagine. Per ulteriori informazioni, vedere [l'importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Poiché è difficile modificare queste pagine, dopo l'importazione, è consigliabile progettare le pagine prima di importarli.  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>Creazione di temi, ECMAScript e fogli di stile CSS  
 Visual Studio fornisce modelli per lo sviluppo fogli CSS (Cascading Style), ECMAScript (JavaScript e JScript) o file di tema per i siti di SharePoint. È possibile creare questi file utilizzando le informazioni disponibili nel SDK di SharePoint o mediante strumenti quali SharePoint Designer.  
  
 È possibile aggiungere questi file per la soluzione direttamente oppure è possibile importarli. In entrambi i casi, è necessario creare le cartelle mappate appropriate per ogni elemento che si aggiunge. Per ulteriori informazioni su come creare una cartella mappata, vedere [procedura: aggiungere e rimuovere cartelle mappata](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Per ulteriori informazioni sulla creazione di fogli di stile CSS, vedere [utilizzo della classe fogli di stile CSS in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Per ulteriori informazioni sulla creazione di un file JavaScript e JScript per una soluzione di SharePoint, vedere [impostazione di una pagina ASPX di base per ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Per ulteriori informazioni su temi, vedere [blocco predefinito: pagine e l'interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Viene descritto come aggiungere le pagine di applicazioni: contenuto aspx unito con una pagina master di SharePoint.|  
|[Procedura: Creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)|Viene illustrato come creare pagine ASP.NET eseguite in un sito di SharePoint.|  
|[Procedura dettagliata: creazione di una pagina di un'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Viene illustrato come progettare ed eseguire il debug di una pagina Web ASP.NET per un sito di SharePoint.|  
  
  