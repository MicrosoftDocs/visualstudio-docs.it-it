---
title: Estensione degli strumenti di SharePoint in Visual Studio | Documenti Microsoft
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
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: db0afa41641cd9d5ae04cfe6d391dbf0fe814f0f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>Estensione degli strumenti di SharePoint in Visual Studio
  Gli strumenti di SharePoint in Visual Studio soddisfano i requisiti di molti scenari di sviluppo di applicazioni. Tuttavia, si potrebbero individuare i casi in cui non dispongono della funzionalità che richiedono di altri sviluppatori. In questi casi, è possibile estendere gli strumenti di SharePoint per creare le funzionalità necessarie.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Come estendere gli strumenti di SharePoint  
 È possibile estendere il sistema di progetto SharePoint e **connessioni di SharePoint** nodo il **Esplora Server** finestra.  
  
### <a name="extending-the-sharepoint-project-system"></a>Estensione del sistema di progetto SharePoint  
 Visual Studio include un set di modelli di progetto e modelli di elemento che è possibile utilizzare per creare soluzioni di SharePoint. Ad esempio, sono disponibili modelli per i ricevitori di eventi, le definizioni di elenco, flussi di lavoro e Web part. Tuttavia, è anche possibile definire i propri tipi di elementi di progetto SharePoint per la creazione di componenti di SharePoint, ad esempio i campi o azioni personalizzate. È inoltre possibile creare estensioni per i tipi di elemento di progetto SharePoint sono già installati in Visual Studio ed è possibile creare estensioni per i progetti SharePoint.  
  
 Per ulteriori informazioni, vedere [estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Estensione del nodo Connessioni di SharePoint in Esplora server  
 In Visual Studio, è possibile utilizzare il **connessioni di SharePoint** nodo il**Esplora Server** consente di visualizzare molti dei componenti di uno o più siti SharePoint locali in una visualizzazione struttura ad albero gerarchica. È anche possibile estendere il **connessioni di SharePoint** nodo nei modi seguenti:  
  
-   Tramite l'aggiunta di nodi personalizzati. Ciò è utile se si desidera visualizzare i componenti dei siti di SharePoint che non vengono visualizzati per impostazione predefinita.  
  
-   Estendendo i nodi esistenti. Ad esempio, è possibile aggiungere un nuovo nodo figlio a un nodo esistente oppure è possibile aggiungere una voce di menu di scelta rapida a un nodo ed eseguire attività quando uno sviluppatore fa clic sulla voce di menu.  
  
 Per ulteriori informazioni, vedere [estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Requisiti del Computer di sviluppo  
 Per creare estensioni per gli strumenti di SharePoint, il computer di sviluppo deve soddisfare gli stessi requisiti per la creazione di soluzioni SharePoint in Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 È inoltre consigliabile installare il [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. il SDK include strumenti e modelli di progetto che è possibile utilizzare per estendere Visual Studio. In particolare, il SDK include un modello di progetto che consente di creare facilmente un pacchetto di Visual Studio Extension (VSIX). Pacchetti VSIX costituiscono il modo migliore per distribuire le estensioni di Visual Studio in Visual Studio. Tutte le estensioni di strumenti di SharePoint devono essere distribuite utilizzando pacchetti VSIX. Tutte le procedure dettagliate di questa documentazione si presuppone la [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installato.  
  
 Per installare Visual Studio SDK, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Per ulteriori informazioni sulle estensioni di Visual Studio, vedere [iniziando a sviluppare estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del modello di programmazione di SharePoint di estensioni degli strumenti](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Guida di riferimento &#40; Estensibilità degli strumenti di SharePoint &#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Estensioni di debug per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  