---
title: Integrazione di dati di Business in SharePoint | Documenti Microsoft
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c054049c09f13c224ee4f0bb3021af1121f5cea8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="integrating-business-data-into-sharepoint"></a>Integrazione di dati business in SharePoint
  È possibile integrare i dati di business in SharePoint. Dati di business possono provenire da applicazioni server back-end, ad esempio [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel e SAP, o un servizio Web. Gli utenti possono visualizzare, aggiungere, aggiornare o eliminare dati di business utilizzando gli elenchi esterni o Web part dei dati di Business in SharePoint.  Gli utenti possono accedere anche questi dati in un'applicazione di Microsoft Office, ad esempio Microsoft Outlook. Per ulteriori informazioni, vedere [dove possibile dati esterni](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Per integrare i dati in SharePoint, creare un modello per il servizio di integrazione applicativa dei dati (BDC). Il servizio di integrazione applicativa dei dati è un'applicazione in SharePoint che archivia le informazioni sui dati nelle applicazioni di business. Per ulteriori informazioni, vedere [servizio di integrazione applicativa dei dati (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modelli di Visual Studio  
 I modelli di Visual Studio consentono di scrivere codice personalizzato per recuperare e aggiornare i dati da origini dati back-end. È inoltre possibile aggregare i dati da più origini dati. Ad esempio, è possibile visualizzare un elenco di clienti che contiene i dati da un [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] database e un servizio Web.  
  
 È inoltre possibile importare i modelli che sono già stati distribuiti in SharePoint. Dopo aver importato un modello, è possibile aggiungere codice personalizzato o semplicemente usare Visual Studio per creare un pacchetto e distribuirlo in più server farm di SharePoint. Per ulteriori informazioni, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="designing-a-model-in-visual-studio"></a>Progettazione di un modello in Visual Studio  
 È possibile progettare un modello utilizzando una finestra di progettazione e finestre degli strumenti diversi. Quando si progetta il modello, Visual Studio genera il codice XML del modello. Per ulteriori informazioni, vedere [panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Un modello contiene entità e i metodi.  
  
### <a name="entities"></a>Entità  
 Un'entità descrive una raccolta di campi. Ad esempio, un'entità può rappresentare una tabella in un database. Un'entità viene visualizzato come un tipo di contenuto esterno in SharePoint. Per ulteriori informazioni sui tipi di contenuto esterni, vedere [quali sono i tipi di contenuto esterno?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Metodi  
 I consumer di un tipo di contenuto esterno per eseguire un'azione per i campi di un'entità consente a un metodo. Ad esempio, un metodo Updater potrebbe consentire agli utenti di modificare l'indirizzo e la data di un cliente di nascita in `Address` e `BirthDate` sono campi del `Customer` entità.  
  
 Visual Studio genera un file di codice del servizio per ogni entità nel modello. Quando si aggiunge un metodo per il modello, Visual Studio genera un metodo corrispondente nel file di codice del servizio. Aggiungere codice a ogni metodo per eseguire l'operazione appropriata. Ad esempio, se si aggiunge un metodo Creator al modello, Visual Studio genera un metodo Creator nel file di codice del servizio. Questo metodo viene chiamato dal servizio di integrazione applicativa dei dati quando un utente sceglie il **nuovo elemento** pulsante in un elenco che è basato sul modello. Pertanto, è possibile aggiungere codice al metodo Creator che aggiungono nuovi dati a un'origine dati. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)|Mostra come creare un nuovo modello o importare un modello che si esporta da SharePoint.|  
|[Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)|Descrive come progettare gli elementi di un modello utilizzando gli strumenti di progettazione di Visual Studio.|  
|[Quando Visual Studio utilizzare SharePoint Designer. Soluzioni di Visual Studio per la compilazione utilizzando BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Consente di decidere se utilizzare Visual Studio o SharePoint Designer per creare un modello per l'integrazione applicativa dei dati.|  
  
  